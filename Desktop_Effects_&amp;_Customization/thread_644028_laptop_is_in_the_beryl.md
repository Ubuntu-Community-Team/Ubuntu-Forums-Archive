---
title: "laptop is in the beryl"
date: 2007-12-18
forum: Desktop Effects &amp; Customization
---

### Post by LT72884 on 2007-12-18
ok here is a screen shot form my laptop. My lap top has the nvidia 7600gt. i know beryl works with this laptop because my boss has it running on his with fedora core 7. as you can see that its all weird and jacked. The crazy thing is that it also does this in regular desktop effects. The pure white screen is my terminal. as you can tell that there are no borders or window management icons such as the X for close and what not. 

[[IMG]http://aycu37.webshots.com/image/36436/2001269691057125873_th.jpg[/IMG]](http://allyoucanupload.webshots.com/v/2001269691057125873)

here is what it looks like with out any desktop effects turned on or beryl

[[IMG]http://aycu16.webshots.com/image/35975/2004565912570511551_th.jpg[/IMG]](http://allyoucanupload.webshots.com/v/2004565912570511551)

Any help to get this working would be nice. i do have the so called restricted driver for nvidia enabled.

Thanks guys

---

### Post by overdrank on 2007-12-20
> **LT72884 said:**
> ok here is a screen shot form my laptop. My lap top has the nvidia 7600gt. i know beryl works with this laptop because my boss has it running on his with fedora core 7. as you can see that its all weird and jacked. The crazy thing is that it also does this in regular desktop effects. The pure white screen is my terminal. as you can tell that there are no borders or window management icons such as the X for close and what not. 

[[IMG]http://aycu37.webshots.com/image/36436/2001269691057125873_th.jpg[/IMG]](http://allyoucanupload.webshots.com/v/2001269691057125873)

here is what it looks like with out any desktop effects turned on or beryl

[[IMG]http://aycu16.webshots.com/image/35975/2004565912570511551_th.jpg[/IMG]](http://allyoucanupload.webshots.com/v/2004565912570511551)

Any help to get this working would be nice. i do have the so called restricted driver for nvidia enabled.

Thanks guys

HI and you may want to add these to your xorg
Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
Backup your xorg first
To copy Xorg
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```
To restore backup
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
Then use the command ```
gksudo gedit /etc/X11/xorg.conf
``` to edit the file

---

### Post by LT72884 on 2007-12-20
> **overdrank said:**
> HI and you may want to add these to your xorg
Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
Backup your xorg first
To copy Xorg
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```
To restore backup
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
Then use the command ```
gksudo gedit /etc/X11/xorg.conf
``` to edit the file


ok i will try that for kicks and giggles but in the past i have never had to do that. ill show you how i did it and it worked at one point in time.
[http://www.maximumpc.com/linux?page=0%2C3](http://www.maximumpc.com/linux?page=0%2C3)

that showed me how to do it and it worked but i reinstalled and it does not work.  so freakin weird

---

### Post by LT72884 on 2007-12-20
forgot to mention one thing, its probably important to. when i added the repos, and did a apt-get update it said that the signitures for those repos were bad and couldnt update.

---

### Post by NateMan on 2007-12-20
what version of ubuntu are you using? I am almost positive that the beryl repos are for 7.04. if your using 7.10 why not use compiz fusion? I imagine that the built in effects don't like beryl being installed too. and if you are using 7.04 then why not just install compiz fusion as it works better for me than beryl ever did.

---

