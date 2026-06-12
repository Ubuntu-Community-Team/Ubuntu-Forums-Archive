---
title: "No graphical effects"
date: 2009-02-10
forum: Desktop Environments
---

### Post by bilol on 2009-02-10
Hi,  
I could not enable the  graphical effects (like **Desktop wall** or **wobbly window**) in my PC (due to my poor graphics card, I suppose).So , I installed *compizconfig*.I Tried to enable them from system> preference> Advanced Desktop Effects Setting.But still I am not getting those efects.However, when I tried *Linux-Mint* live cd , I was getting those graphical effects. 
How will I be able to get those graphical effects in Ubuntu(Hardy) ? 
Need your suggestion........

---

### Post by null.byte on 2009-02-10
System > Preferences > Appearance > Visual Effects > Tick "Extra".

---

### Post by bilol on 2009-02-10
Hi,
> System > Preferences > Appearance > Visual Effects > Tick "Extra". 
Can not enable "Extra" due to my slow graphics card.

---

### Post by mocoloco on 2009-02-10
If the effects worked under Mint but not Ubuntu then you probably need to install the correct graphics driver under Ubuntu.  Go to System -> Administration -> Hardware Drivers.  Install the graphics driver it mentions there if any (if it has more then one install the recommended one).
If there aren't any drivers listed, open a terminal (Applications -> Accesories -> Terminal) and type lspci.  Paste in what it lists about your graphics card.

---

### Post by bilol on 2009-02-11
Hi mocoloco,
When I use System -> Administration -> Hardware Drivers
It shows the following driver:
[I]ATI accelerated graphics driver
[/I]
But I can not enable it.It yields the following error:
```
W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/xorg-driver-fglrx_7.1.0-8-3+2.6.24.13-18.41_i386.deb
  Could not resolve 'security.ubuntu.com'
```
I suppose,I am getting this error as the Pc (in which the problem is faced) is offline.
Next, I did the following ,as you told me to do:
```
bilol@bilol-desktop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

---

### Post by bilol on 2009-02-11
I have downloaded 
[I]xorg-driver-fglrx_7.1.0-8-3+2.6.24.14-22.53_i386.deb
xorg-driver-fglrx_7.1.0-8-3+2.6.24.16-23.56_i386.deb[/I]
But I did not get
*xorg-driver-fglrx_7.1.0-8-3+2.6.24.13-18.41_i386.deb*
Will I try to install both of them(or one of them) in that  offline machine?

---

### Post by mocoloco on 2009-02-13
No, you will need to download and install the correct one for your Kernel.  I have a link :[http://launchpadlibrarian.net/14932056/xorg-driver-fglrx_7.1.0-8-3%2B2.6.24.13-18.41_i386.deb]("http://launchpadlibrarian.net/14932056/xorg-driver-fglrx_7.1.0-8-3%2B2.6.24.13-18.41_i386.deb")
(Taken from [launchpad]("https://launchpad.net/ubuntu/hardy/i386/xorg-driver-fglrx/1:7.1.0-8-3+2.6.24.13-18.41")).
Just double click it and follow the instructions to install.  After you install it you might need to run *Hardware Drivers* again to enable it, and then be requested to reboot.

---

### Post by bilol on 2009-02-16
Hi,
> Just double click it and follow the instructions to install. After you install it you might need to run Hardware Drivers again to enable it, and then be requested to reboot. 
I have installed the package,then run the hardware driver again and reboot the system.But everything was in vain.No graphical effects took place,However as the window size of Ubuntu get diminished abruptly, I have to uninstall the package again.
What should I do?
Please note that when I tried Linux-mint Live cd ,every graphical effects took place without any problem.

---

### Post by bilol on 2009-02-18
Is there anyone faced the same problem?
need your valuable suggestion....

---

### Post by Pants Dance on 2009-02-23
Hey, I'm having a similar problem.  I posted about it elsewhere, but didn't get a response.  I have no graphical effects or workspaces and I can't get CompizConfig to work.  My screen is also stuck on the wrong aspect ratio, which is a pain, and any screensavers are running really badly.
  Thing is that all this used to work, prior to plugging my laptop into an LCD TV and playing with the settings.  I think all I need to do is reset my hardware or driver settings, and reinstall Compiz.  Is there anyone who knows how to do this?
  Also, when trying to turn the effects to "extra", I just got told I couldn't, which is odd because, as I said, it all worked before.

---

### Post by mocoloco on 2009-02-23
bilol, what do you mean when you say the windows size is diminished abruptly? Do the window decorations dissapear (the border around the window, and the top title bar)?

---

