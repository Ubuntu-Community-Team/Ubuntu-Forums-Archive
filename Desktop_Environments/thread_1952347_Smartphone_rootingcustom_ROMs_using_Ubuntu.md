---
title: "Smartphone rooting/custom ROMs using Ubuntu"
date: 2012-04-04
forum: Desktop Environments
---

### Post by mbnickson on 2012-04-04
Right, i'm fairly new to Ubuntu and use it as my sole OS on my desktop pc at home because Windows Vista was killing my pc.
 
I have a Motorola Defy smartphone running android Eclair (2.1) and would like to root it and put a custom rom on it.  The problem i'm having is that all the guides for rooting the phone make the assumption that you use windows.  
 
Can anyone give me any advice as to how i might root my phone whilst using Ubuntu?  Are there any projects ongoing in the Ubuntu world which specialise in smartphone rooting software? Or do you think it's something that could be incorporated into Ubuntu by default in the future? It's a bit of an emerging market and i eagerly await the launch of UbuntuforAndroid or just plain Ubuntu on my smartphone but this might be a while away yet.
 
My initials thoughts are that i could use the windows programs in WINE but i'm reluctant to do that because of the security issues surrounding WINE.
 
Any advice anyone?
Mike

---

### Post by irw on 2012-04-04
you cannot do this via wine due to lack of usb support.

I have a defy and have flashed new roms and rooted my phone from Ubuntu.

Unfortunately I do no have any of the details here, but I found all I needed via google and particularly the fora at xda-developers.com

The info is out there - just not always easy to find!

---

### Post by huggs on 2012-04-04
If you don't have any access to a Windows machine, the only option you will have in Ubuntu is to run a Windows virtual machine to root/flash your phone. I'm guessing it won't just work straight away, you'll probably have to mess around and configure and experiment with it. 

Seems like a pretty good way to accidentally brick your phone to me. I'd just borrow a friend's Windows machine.

---

### Post by ccrs8 on 2012-04-04
I don't have a defy, but I have plenty of experience rooting and installing custom recoveries and custom ROMs on Android phones (Samsung Moment, LG Optimus S, Nexus S).  The vast majority of the things you need to do can be done on Ubuntu with the Android SDK (and ADB specifically) installed.  Sometimes ROM devs or other modders will make things simpler by automating various commands by putting them in a Windows .bat file, but you can run those commands manually in Ubuntu.  That being said, there are a few things (mostly dealing with loading new radio files) that you simply need to use a Windows utility for.  I find that Wine and VirtualBox are not sufficient - you need a real Windows box.

---

### Post by fjouanel on 2012-05-20
Since Android runs on Linux, shouldn't there be an easier way than to use Windows? I am having the same problem, and I do not feel like using windows.

---

### Post by rmjones85 on 2012-05-20
Try: [http://forum.xda-developers.com/archive/index.php/t-853672.html](http://forum.xda-developers.com/archive/index.php/t-853672.html)

They have the best guides around.

---

