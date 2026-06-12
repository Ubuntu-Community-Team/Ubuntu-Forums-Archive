---
title: "Xubuntu 16.04 ttyname failed Inappropriate ioctl for device"
date: 2017-08-16
forum: Desktop Environments
---

### Post by chrischarles2002 on 2017-08-16
I have a need to launch Xubuntu as a **ROOT **user for a stand-alone demo system.


Whether I use the auto-login feature from **lightdm**, or when logging in via "Other" > "root" when prompted, I always get the following response:


    ```
Error found when loading /root/.profile
    mesg: ttyname failed: Inappropriate ioctl for device
    As result the session will not be configured correctly.
    You should fix the problem as soon as feasible.
```


[SCREENSHOT HERE]([http://imgur.com/a/iW5Jt](http://imgur.com/a/iW5Jt))


***After clearing the popup box above, the system performs as expected with the ROOT user.***


Here are the contents of `/etc/lightdm/lightdm.conf`:


    ```
[Seat:*]
    autologin-guest=false 
    autologin-user=root
    autologin-user-timeout=0
```


I have seen other similar issues online relating to Valgrind, and that the issues was solved with some of the latest updates, but this still seems to be happening on Xubuntu 16.04


[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1584488](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1584488)


[https://superuser.com/questions/1160025/how-to-solve-ttyname-failed-inappropriate-ioctl-for-device-in-vagrant](https://superuser.com/questions/1160025/how-to-solve-ttyname-failed-inappropriate-ioctl-for-device-in-vagrant)


Most forums state that this message is erroneous and should not be displayed.
Is there anyway to launch Xubuntu automatically as root while avoiding this erroneous popup?

---

