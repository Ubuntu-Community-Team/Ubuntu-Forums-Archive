---
title: "no graphical login / lightdm killed"
date: 2012-09-26
forum: Desktop Environments
---

### Post by KisteBecks on 2012-09-26
hi,

i tried to reset my lightdm configs with:
```

dpkg --force-all --purge lighdm
apt-get install lightdm

```but now sudo /etc/init.d/lightdm  wont do anything besides show the boot
messages on tty6. theres nothing on tty7.
theres also no error even if lightdm is started manually without the init scripts.
im currently running "x" with startx and gnome-terminal as first application in  ~/.xinitrc.
any idea how i can get the problem solved so that i can login again normally?

cant even move windows around :(

---

### Post by Argenteus on 2012-09-26
Try
```
dpkg-reconfigure lightdm
```
Also, did you misstype and mean sudo apt-get install? If not, try installing again with sudo, you need root access to install applications.

---

### Post by KisteBecks on 2012-09-27
yes i do work with sudo when required, in this case i just didnt write it down.
sadly the reconfigure did not create a chance :(

this was missing:
 ```

/etc/lightdm/lightdm.conf 
[SeatDefaults]
allow-guest=false
user-session=ubuntu
greeter-session=unity-greeter

```

quesiton: why did apt not install the file a second time after a purge?

---

