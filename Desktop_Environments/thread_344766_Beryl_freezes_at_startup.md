---
title: "Beryl freezes at startup"
date: 2007-01-23
forum: Desktop Environments
---

### Post by miceagol on 2007-01-23
I just installed Beryl according to [this guide]("http://www.ubuntuforums.org/showthread.php?t=263851"). First Beryl didn't work, though Beryl Manager showed up in the gnome panel. I saw an error message about composite being disabled in the terminal, and fixed it by changing that to enabled in xorg.conf. But now Beryl freezes my entire system when I try to start it. Its output is as follows before everything goes into freeze mode:
```

XGL absent, checking for NVIDIA
NVIDIA present
Relaunching beryl unit _GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
NVIDIA present

```
All I can do is a Ctrl+Alt+SysRq SUB, but I can move the mouse. Any suggestions?

---

### Post by chipdip on 2007-01-23
I have the same problem, after updating Beryl to the newest in the repos, it just freezes on startup.

---

### Post by rkrizan on 2007-01-23
I have a problem with it becomming totally blurry, and I can't do anything with it.

---

### Post by miceagol on 2007-01-23
Hmm... Maybe we should revert to the previous version. :-?

---

### Post by miceagol on 2007-01-31
Bump! 

Still need help with this. I've tried to disable composite again, which makes it possible for Beryl Manager to at least load. But metacity is the selected window manager as default. When I try to change this to Beryl, the borders on the windows just flash a couple of, and are then reverted back to normal and metacity is again selected.

---

### Post by miceagol on 2007-02-01
Managed to fix it guys. :D Do as follows:

1. Edit your .beryl/settings, and change "s_sync_to_vblank" to false.
2. If you've got no window borders, also do this in beryl-manager: Advanced -> Rendering path -> Copy
3. You've got Beryl! :D

---

### Post by glabouni on 2007-02-01
[http://ubuntuforums.org/showthread.php?t=351319](http://ubuntuforums.org/showthread.php?t=351319)

---

### Post by zinko_pt on 2007-02-12
Sorry for geting into the discussion, but I never managed for Edgy to run LiveCD on my new rig:
C2D E6600
Asus P5B Deluxe
2GB Team Elite 6400 CL5
Asus 8800GTS

Theres always a X server error and I cannot pass it. I did managed to install OpenSuse, but I dont like it.

I have Edgy on a ACER 8003LMi and on a P4@1.6GHz desktop, and they always worked fine, with internet, burning, wireless, 3Ddesktop, etc.

I supose it has something to do with 8800GTS conected by DVI to a Samsung940BW.

I noticed some of you have the same MoBo and the same graphics chipset. Can you help me with this? I dont want to give up Ubuntu, although Im still a noob.

Thx

---

### Post by miceagol on 2007-02-13
> **zinko_pt said:**
> Sorry for geting into the discussion, but I never managed for Edgy to run LiveCD on my new rig:
C2D E6600
Asus P5B Deluxe
2GB Team Elite 6400 CL5
Asus 8800GTS

Theres always a X server error and I cannot pass it. I did managed to install OpenSuse, but I dont like it.

I have Edgy on a ACER 8003LMi and on a P4@1.6GHz desktop, and they always worked fine, with internet, burning, wireless, 3Ddesktop, etc.

I supose it has something to do with 8800GTS conected by DVI to a Samsung940BW.

I noticed some of you have the same MoBo and the same graphics chipset. Can you help me with this? I dont want to give up Ubuntu, although Im still a noob.

Thx

You need to download the latest nvidia-drivers (97.46) to get 8800GTS to work. All you have to do is to follow method 2 of [this guide]("http://doc.gwos.org/index.php/Latest_Nvidia_Edgy"). You need to do this from the console, so just exit from the X server blue screen. If you don't see the console after that, press Ctrl + Alt + F1. I don't know if the Asus P5B Deluxe has the same network card as on my mobo, but mine didn't work after installation. If yours doesn't work you need to download the nvidia drivers with another PC, and put it on e.g. a flash disk. 

Yet another thing :) The flash disk might not mount when you insert it. If so, you need to check dmesg for its location. Check one of the last messages of the output. You should see something like sda1 or similar. Then type the command:
```

mount -t vfat /dev/<location> /media/usbdisk

``` 
where <location> must be replaced with what you found in dmesg. Now you may copy the nvidia driver to your home folder, and install it using the guide above.

All this happens because the 8800-series cards came after the Edgy Eft release, so this won't be a problem when Feisty Fawn is released. :KS 

Tell us how it goes!

---

### Post by miceagol on 2007-02-13
And of course, I forgot that you haven't even installed it yet. You must install Ubuntu using the [alternate CD]("http://neacm.fe.up.pt/pub/ubuntu-releases/edgy/ubuntu-6.10-alternate-i386.iso") unfortunately. It's a non-GUI installation where you must answer more questions during the installation. Install it, and use my guide above when you try to launch Ubuntu after installation.

Remember that you won't get into these troubles when Feisty comes, so don't give up. ;)

---

### Post by zinko_pt on 2007-02-13
Thanks for your patience. I will give it a try, although I already tried Feisty Alpha4 and it didn’t work as also, at least from the Live CD.

Actually, I tried (and failed) the following:
Ububtu606LiveCD
Ubuntu610LiveCD
Kubuntu606LiveCD
LG3D 2.3 LiveCD
Caixa Mágica11 (portuguese flavour)
Free BSD6.1CD
Slackware11
UbuntuLite1.1

The only one that worked "out-of-the-box" was OpenSuse, but it assumed a VESA card and the fonts were "blur".

It seems to me that Linux has WAY better choices for old hardware, but when it comes to "fresh" HW, Windows still rules. It is hard for me to admit it but that’s the evidences: games and hardware support.

Nevertheless I will post my efforts within some hours. And I think you’re right the NIC never worked in any of the above "flavours", except OpenSuse.

---

### Post by miceagol on 2007-02-14
> **zinko_pt said:**
> 
The only one that worked "out-of-the-box" was OpenSuse, but it assumed a VESA card and the fonts were "blur".

It seems to me that Linux has WAY better choices for old hardware, but when it comes to "fresh" HW, Windows still rules. It is hard for me to admit it but that’s the evidences: games and hardware support.


When it comes to nVidia graphics drivers, Windows isn't THAT much better than Linux. You also have to download and install drivers there. I installed Vista a month ago, and there was no driver at all for the 8800GTS, but there was one for Linux. ;)

The only thing that's better is that you don't end up in a non-GUI interface when there's no driver for your card. It falls back on VESA instead. OpenSuse did that, and that's very good. I hope this will also be done with other Linux distros in the future. It's terrible for newbies when they end up with a blue screen, before they've even tried the Live CD.

---

### Post by zinko_pt on 2007-02-15
Well, thanks for your support, but its a big pain in the a** to get all things working.

To install the 8800 driver, I would need first to get libc development package. Because that's the stated message when I try to install it.

But to get libc I would need the Marvell network controller working.

But to get that working I would need...

Its just too much.

Well if anyone care to explain me how I install the NIC driver I would appreciate. Even the directories stated at the readme are wrong:
[]("http://dlsvr01.asus.com/pub/ASUS/lan/marvell/8056/8056_8001_Linux.zip")[http://dlsvr01.asus.com/pub/ASUS/lan/marvell/8056/8056_8001_Linux.zip](http://dlsvr01.asus.com/pub/ASUS/lan/marvell/8056/8056_8001_Linux.zip)

If not, I will be a Windows user at home, hopping that Feisty will solve the problems for me.

Thanks

---

### Post by miceagol on 2007-02-18
> **zinko_pt said:**
> Well, thanks for your support, but its a big pain in the a** to get all things working.

To install the 8800 driver, I would need first to get libc development package. Because that's the stated message when I try to install it.

But to get libc I would need the Marvell network controller working.

But to get that working I would need...

Its just too much.

Well if anyone care to explain me how I install the NIC driver I would appreciate. Even the directories stated at the readme are wrong:
[]("http://dlsvr01.asus.com/pub/ASUS/lan/marvell/8056/8056_8001_Linux.zip")[http://dlsvr01.asus.com/pub/ASUS/lan/marvell/8056/8056_8001_Linux.zip](http://dlsvr01.asus.com/pub/ASUS/lan/marvell/8056/8056_8001_Linux.zip)

If not, I will be a Windows user at home, hopping that Feisty will solve the problems for me.

Thanks

What exactly don't you understand from the README? 

I think I managed to install the nVidia driver without being connected to the Internet. Try running it again after it fails the first time. And if you can, try ignoring the error messages you get, just to get the drivers installed.

This is a pain in the ***, I agree, but at least this shouldn't be happening in future releases.

---

### Post by pastaq on 2007-03-01
wow. i cant believe the problem was that simple. >< I wasted 8 hours trying to get my 8800GTS to work with beryl with pretty much everything i could think of. Thanks a lot, you should put this in the wiki on the beryl site.

---

