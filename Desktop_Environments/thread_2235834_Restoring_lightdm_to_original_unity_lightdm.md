---
title: "Restoring lightdm to original unity lightdm"
date: 2014-07-23
forum: Desktop Environments
---

### Post by izurdo on 2014-07-23
Hi team,
I have a laptop with Ubuntu 14.04 LTS (clean install, do not like updates) and I installed xubuntu-desktop just to try it.
The problem is that I really do not like it changed my original lightdm configuration to xubuntu lightdm configuration. I want the original ubuntu unity lightdm. I've been looking here and other sites and found no solution, the file people refers do not exist anymore in 14.04. Here are the config files I have:
```
$ locate lightdm.conf
/etc/init/lightdm.conf
/etc/lightdm/lightdm.conf.d
/etc/lightdm/lightdm.conf.d/10-xubuntu.conf
/usr/share/doc/lightdm/lightdm.conf.gz
/usr/share/lightdm/lightdm.conf.d
/usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
/usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
/usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
/usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
/usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
/usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
/var/lib/dpkg/info/lightdm.conffiles
/var/lib/dpkg/info/lightdm.config


```

Thanks and best regards

---

### Post by deadflowr on 2014-07-23
Do you mean the greeter session?
From here [https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)
as explained, the system uses the files in /usr/share/lightdm/lightdm.conf.d/ by default.
But you can overrides these by setting a folder and files in /etc/lightdm/lightdm.conf.d/.

I would do the following.
Easiest for me is a terminal way
```
sudo nano /etc/lightdm/lightdm.conf.d/10-mylogin.conf
```
then add 
```

[SeatDefaults]
greeter-session=unity-greeter

```
You can also follow the wiki for more entires if you'd like.
Then ctrl +x to save and close.
The new settings should appear upon a reboot.
(Might only take a log out, but I'm not sure)

I would also move the 10-xubuntu.conf entry, perhaps something like
```
sudo mv /etc/lightdm/lightdm.conf.d/10-xubuntu-conf /etc/lightdm/lightdm.conf.d/10-xubuntu-conf.bak
```
or remove the entry entirely, if you want.

Hope this helps.

---

