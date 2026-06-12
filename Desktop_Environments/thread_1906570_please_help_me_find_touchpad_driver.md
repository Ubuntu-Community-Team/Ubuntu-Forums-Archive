---
title: "please help me find touchpad driver"
date: 2012-01-09
forum: Desktop Environments
---

### Post by dannodan2008 on 2012-01-09
hi there guys,
 I really need some help. a few days ago my touchpad has stopped working  after an update in the latest ubuntu. It is working in win7 (dual boot)  so i know its not a hardware fault. My pal at work says it is probaly a  driver issue. Ok so today i went and brought a mouse and have been  trying to fix this. But i am in way over my head, Im a total noob when  it comes to linux. PLEASE PLEASE PLEASE could someone give me step by  step instructions on how to find and update my touchpad driver . i am  running a hp pavillion dv7 ( [http://en.gentoo-wiki.com/wiki/HP_Pavilion_dv7-1080](http://en.gentoo-wiki.com/wiki/HP_Pavilion_dv7-1080) ). im dual booting the latest ubuntu and win 7.
Guys your my last hope before turning back to the dreaded windows :sad:
Regards and thanks for taking the time to read this
Danno

---

### Post by dannodan2008 on 2012-01-09
PLEASE PLEASE help !:(

---

### Post by jmate24 on 2012-01-11
is it an apple touchpad?
also you might want to try and install this in a terminal (Ctrl+Alt+t) Enter this command (copy and paste is OK too but be careful and avoid any "rm *anything*" commands and always double check with someone else if the command or "bash script" will harm your computer and data.) 
hit enter or return then type your log-on passoword:

```
sudo apt-get install xserver-xorg-input-multitouch xserver-xorg-input-mutouch xserver-xorg-input-penmount [xserver-xorg-input-joystick
```

If this does not work then I will bookmark your thread and check in with you on wendsday january 11 USA. to see if that fixed the problem. you might also want to try to un-plug and re-plug in the mouse.

---

### Post by airplanesimen on 2012-01-11
> **jmate24 said:**
> is it an apple touchpad?
also you might want to try and install this in a terminal (Ctrl+Alt+t) Enter this command (copy and paste is OK too but be careful and avoid any "rm *anything*" commands and always double check with someone else if the command or "bash script" will harm your computer and data.) 
hit enter or return then type your log-on passoword:

```
sudo apt-get install xserver-xorg-input-multitouch xserver-xorg-input-mutouch xserver-xorg-input-penmount [xserver-xorg-input-joystick
```

If this does not work then I will bookmark your thread and check in with you on wendsday january 11 USA. to see if that fixed the problem. you might also want to try to un-plug and re-plug in the mouse.

I have the DV7 from HP, and it is not an apple touchpad. This will solve your problem:

[http://ubuntuforums.org/showthread.php?t=1663324](http://ubuntuforums.org/showthread.php?t=1663324)

---

### Post by airplanesimen on 2012-01-11
> **dannodan2008 said:**
> hi there guys,
 I really need some help. a few days ago my touchpad has stopped working  after an update in the latest ubuntu. It is working in win7 (dual boot)  so i know its not a hardware fault. My pal at work says it is probaly a  driver issue. Ok so today i went and brought a mouse and have been  trying to fix this. But i am in way over my head, Im a total noob when  it comes to linux. PLEASE PLEASE PLEASE could someone give me step by  step instructions on how to find and update my touchpad driver . i am  running a hp pavillion dv7 ( [http://en.gentoo-wiki.com/wiki/HP_Pavilion_dv7-1080](http://en.gentoo-wiki.com/wiki/HP_Pavilion_dv7-1080) ). im dual booting the latest ubuntu and win 7.
Guys your my last hope before turning back to the dreaded windows :sad:
Regards and thanks for taking the time to read this
Danno

Hello!! I found the website where i did download drivers, Check this out first: synaptics drivers for ubuntu (i386) 

[http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html](http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html)

Here is how to get windows drivers in ubuntu:
[http://drivers.downloadatoz.com/tutorial/29074,how-to-use-windows-drivers-in-ubuntu.html](http://drivers.downloadatoz.com/tutorial/29074,how-to-use-windows-drivers-in-ubuntu.html)

---

### Post by dannodan2008 on 2012-01-12
Guys thank you so much ! !
my ubuntu is fine and dandy again :-)
Thanks for taking the time to help me
Danno

---

### Post by airplanesimen on 2012-01-12
> **dannodan2008 said:**
> Guys thank you so much ! !
my ubuntu is fine and dandy again :-)
Thanks for taking the time to help me
Danno

no problem :P Go to thread tools at top of this page, and mark this thread as [solved] :P
good luck further!

---

