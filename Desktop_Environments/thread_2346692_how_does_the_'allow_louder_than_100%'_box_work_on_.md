---
title: "how does the 'allow louder than 100%' box work on ubuntu 14.04?"
date: 2016-12-17
forum: Desktop Environments
---

### Post by ubto66 on 2016-12-17
[https://imgur.com/aC3FWMZ](https://imgur.com/aC3FWMZ)
This sound setting is available in ubuntu 14.04 gnome 3.14.
On ubuntu 16.04 mate it is not.

I want to know, how does the 'allow louder ...' achieve to set a volume level such that you on the menu bar sound icon can scroll up to a volume level above 100%?

What file in pulseaudio, if it is pulseaudio that sets the volume level you may scroll up to, does the 'allow louder ...' edit?

Thank you.

---

### Post by minecraft-electricity on 2016-12-19
Hi ! 
I think you can do it by installing ubuntu 16.04 LTS parameters package.
There should not be any consequences so try :
```
sudo apt update && sudo apt upgrade && sudo apt install unity-control-center
```
that command will; update your package list, update your packages and then install the unity-control-center, wich controll the sound.
If you got no problem you can open the sound parameters with the command
```
unity-control-center sound
```

---

### Post by ubto66 on 2016-12-22
Thank you. Is installing unity-control-center installing a part of the unity desktop? 
I would like to avoid the unity desktop.

You cannot say in what file the 'allow louder than ...' volume level is set?

---

