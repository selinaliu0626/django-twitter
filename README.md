# django-twitter

core design

Twitter

Core design

![Uploading Screenshot 2023-09-20 at 7.34.14 PM.png…]()

Set Django with Multipass(With Mac)
## 1. install multipass

### 1.1b install multipass with brew
```shell
brew install --cask multipass
```
## 1.2. Verify you installed multipass successfully

```shell
multipass find
```
output should be similar to below
```shell
Image                       Aliases           Version          Description
18.04                       bionic            20221014         Ubuntu 18.04 LTS
20.04                       focal             20221018         Ubuntu 20.04 LTS
22.04                       jammy,lts         20221101.1       Ubuntu 22.04 LTS
anbox-cloud-appliance                         latest           Anbox Cloud Appliance
charm-dev                                     latest           A development and testing environment for charmers
docker                                        latest           A Docker environment with Portainer and related tools
jellyfin                                      latest           Jellyfin is a Free Software Media System that puts you in control of managing and streaming your media.
minikube
```

## 2. run the first script
```shell
# curl -L -o script1.sh 'https://raw.githubusercontent.com/byegates/twitter2/main/script1.sh'
cd ~
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/byegates/twitter2/main/script1.sh)" | tee script1.txt
```

## 3. use SSH log in your Ubuntu vm
ssh ubuntu@192.168.64.1 -i ~/.ssh/multipass-ssh-key -o StrictHostKeyChecking=no

## 4. about mount
### check your vm
ls ~/Home
### the output should be the entire home in your vm, if failed, you can try mount again
```shell
multipass set local.privileged-mounts=Yes
multipass unmount lts2204:Home
multipass mount $HOME lts2204:Home
```
## 5 run your script2.sh
⚠️⚠️⚠️script1 output also told you how to run the second script, just follow the instruction⚠️⚠️⚠️
Basically, it looks like this:
```shell
cd ~
bash script2.sh
```
if you can not find the script2, try:
```shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/byegates/twitter2/main/script2.sh)" | tee script2.txt
```
## 6. everytime when you log in ubuntu, use this command to enter your home folder
```shell
cd ~/Home/github/twitter
```
## Active your python vitual enviroment
```shell
source ~/.virtualenvs/twitter2/bin/activate
```
⚠️⚠️⚠️ every time when you need to log in this environment, you need to run this command

## 7. Change your database setting in settings.py 
```shell
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'twitter',
        'HOST': 'localhost',
        'PORT': '3306',
        'USER': 'root',
        'PASSWORD': 'yourpassword',
    }
}
```
## 8 try to run your project
```shell
python manage.py runserver 0.0.0.0:8000&
```
## 9. visited your website
```shell
192.168.64.1:8000
```

