---
title: "Dell Inspiron 1100 LCD Montior Bug"
date: 2009-08-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by surg34 on 2009-08-09
Hello, world! First post to the forum.  I need some valuable help with this Inspiron 1000 because I'm trying to install 9.0.4 and can't get it working. The LCD monitor crashes after booting up. Have tried these threads:
[http://ubuntu-utah.ubuntuforums.org/showthread.php?p=3821096](http://ubuntu-utah.ubuntuforums.org/showthread.php?p=3821096)
[http://ubuntuforums.org/showthread.php?t=1007754](http://ubuntuforums.org/showthread.php?t=1007754)

I've edited my xorg.conf to this:
[COLOR=Blue]Section "Monitor"
        Identifier      "Generic Monitor"
        ModelName       "Dell 1024x768 Laptop Display Panel"
        HorizSync       31.5 - 48.5
        VertRefresh     59.0 - 75.0
        Option          "DPMS"
EndSection

Section "Device"
        Identifier      "Videocard0"
        Driver          "i810"
        VendorName      "Videocard vendor"
        BoardName       "Intel 845"
        VideoRam                        10000
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubsection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection
[/COLOR]Initialy, I tried installing Kubuntu, but had no luck. When I boot with this, there is a keyboard error. And I've also gotten a "Fatal Error: No Screen Found" on the xorg0.conf log. If I hit escape during the boot up, I'll choose recovery mode-->autofix(?) video display-->then resume normal boot. This usually works(not always). I'd really love to install KUBUNTU instead...but Ubuntu has worked this far...

Bios is A32 via A06
256MB
Celeron

---

### Post by shadetree1 on 2009-08-23
Hi, 

I have the same Dell notebook, with the same issue.

Tried:

Kubuntu first, Live CD failed black screen.
Ubuntu second, Live CD failed black screen.
Gento as last resort, was able to run Live CD but no driver for i82845g adapter to install.
Didn't know what  wget link to download the driver.  Hoping to use the driver with Ubuntu.  

Have searched here and web with no solutions for a new beginner to Linux.

Hope you receive a reply to help me too.

shadetree :confused:

---

### Post by Mewto on 2009-09-14
Hi, There,

I have exactly the same problem with the same laptop.  I sort of have some idea, but I need some help to get it to work with *butu's. I started to try various Linux distro.   

  - None of Ubuntu 9.04 family of distro works, Ubuntu, Xbutu, etc.
  - Text mode always works but it only uses the smaller section of the screen in the middle like the BIOS does.

The only one I found to work is Red Hat 9.  It is pretty old but I just happen to have a set of CDs around. If you install in text mode (linux text) at "boot:" prompt, or if you install it as a "server".   These two work because install will pause to ask me what graphic card I have (which it correctly identified as Intel G82845, but it could not figure out the monitor.  I can select the monitor as "Dell LCD 1024x768" in the next screen or prompt.  That identification of what the monitor is makes it work.   

Well, it is not quite what I want.   The kernel/gcc etc. are simply too too old.  I have trouble install some SW I want to run.   Another problem is that it did not recognize my NIC.  That was easy to fix but still a hassle.   

The Question for Unbutu experts:  What do I let the kernel know what kind of monitor I have?   Please help!

---

### Post by shadetree1 on 2009-09-14
Hi,  I went backward and tried Hardy with success. :P  But I am wondering what will happen with the next Lt version. :confused:  I am learning the difference now so I can con-fig for the newer distros. ;)
 
Hope you all well.:lolflag:
 
shadetree

---

### Post by Mewto on 2009-09-14
I have an Inspiron 1100 but I am also a display problem.   Did you eventually get it resolved?

As you might saw my earlier post that it does work for Red Hat 9, the key seems to be to set the monitor correctly.  The XF86Config.txt on this RH9 actually looks a lot like yours.  But I don't profess know XF86Config well enough to say if a small change makes any difference.  In any case, the Sections defining the monitor and video card on the RH9 are the following:

```

Section "Monitor"
        Identifier   "Monitor0"
        Vendor Name  "Monitor Vendor"
        ModelName    "Dell 1024x768 Laptop Display Panel"
        HorizSync    31.5 - 90.0
        VertRefresh  59.0 - 75.0
        Option       "dpms"
EndSection

Section "Device"
        Identifier   "Videocard0"
        Driver       "i810"
        VendorName   "Videocard vendor"
        BoardName    "Intel 845"
        VideoRam     16384
EndSection

```   

I don't think it hurts to experiment with different settings as long as you use **startx**. 

I decided to leave it at RH9.  The kernel is old (2.4.20-8).   It gives me a chance to try building and upgrading the kernel.  

Still, it would be nice to know how to set up Ubuntu on this laptop.....
 


> **surg34 said:**
> Hello, world! First post to the forum.  I need some valuable help with this Inspiron 1000 because I'm trying to install 9.0.4 and can't get it working. The LCD monitor crashes after booting up. Have tried these threads:
[http://ubuntu-utah.ubuntuforums.org/showthread.php?p=3821096](http://ubuntu-utah.ubuntuforums.org/showthread.php?p=3821096)
[http://ubuntuforums.org/showthread.php?t=1007754](http://ubuntuforums.org/showthread.php?t=1007754)

I've edited my xorg.conf to this:
[COLOR=Blue]Section "Monitor"
        Identifier      "Generic Monitor"
        ModelName       "Dell 1024x768 Laptop Display Panel"
        HorizSync       31.5 - 48.5
        VertRefresh     59.0 - 75.0
        Option          "DPMS"
EndSection

Section "Device"
        Identifier      "Videocard0"
        Driver          "i810"
        VendorName      "Videocard vendor"
        BoardName       "Intel 845"
        VideoRam                        10000
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubsection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection
[/COLOR]Initialy, I tried installing Kubuntu, but had no luck. When I boot with this, there is a keyboard error. And I've also gotten a "Fatal Error: No Screen Found" on the xorg0.conf log. If I hit escape during the boot up, I'll choose recovery mode-->autofix(?) video display-->then resume normal boot. This usually works(not always). I'd really love to install KUBUNTU instead...but Ubuntu has worked this far...

Bios is A32 via A06
256MB
Celeron

---

### Post by shadetree1 on 2009-09-14
Hi again,  
 
You guys could install Hardy and then add the KDE desktop to ubuntu, with or without Gnome's desktop.
 
A bit of advice,  I have had nothing but trouble with the KDE Wifi, it's buggy.  But if you use Ethernet it's fine. 
 
I do like the look & feel of the KDE desktop.  This is coming from a few week old Linux user.:lolflag:
 
shadetree

---

### Post by Mewto on 2009-09-15
I am glad to get some feedback.   I am doing well, how about yourself? 

I tried 8.04 before and it had the same problem on this laptop.   That is Hardy, right?  I have not tried different installation options back then.   Do you have to build in any specific way to get it to work?  I might have to do that with mine.   The old RH9 works and would be there for a while as practice for upgrades.   But I suspect that there needs to have too many upgrades.  Eventually, I would like to know all these enough to get a somewhat updated Linux install on it.  

BTW.  I had the same problem trying to put Windows XP Home back on as well.  After the initial "Press any key to boot from CD" message, the screen went blank just like Fedora 11 Live CD, Ubuntu 8.04, 9.04 Live CD, ... all did (The details might be different but they all look the same to my undiscerning eyes)

---

### Post by shadetree1 on 2009-09-15
> **Mewto said:**
> I am glad to get some feedback. I am doing well, how about yourself? 
 
I tried 8.04 before and it had the same problem on this laptop. That is Hardy, right? I have not tried different installation options back then. Do you have to build in any specific way to get it to work? I might have to do that with mine. The old RH9 works and would be there for a while as practice for upgrades. But I suspect that there needs to have too many upgrades. Eventually, I would like to know all these enough to get a somewhat updated Linux install on it. 
 
BTW. I had the same problem trying to put Windows XP Home back on as well. After the initial "Press any key to boot from CD" message, the screen went blank just like Fedora 11 Live CD, Ubuntu 8.04, 9.04 Live CD, ... all did (The details might be different but they all look the same to my undiscerning eyes)
 
Strange...what I did pre 8.04 was first was check/fix the file system, then defrag and then updated the bios to A32.  Everything installed fine after that.
 
Once installed I could update and change to what ever i wanted.:P
 
shadetree

---

### Post by DougalLongfoot on 2009-09-17
I seem to have gotten my new installation over this bug (crosses fingers). All I did was update the BIOS to A32 and also went to System>Administration>Synaptic Package Manager. Once the package manager was open, did a quick search for i915, and reinstalled xserver-xorg-video-intel since then I haven't had the black screen on startup.

I was wondering if anyone could get anything happening in the System>Preferences>Display panel though. I open it, but there is nothing to see and I can't change any options.

---

### Post by shadetree1 on 2009-09-17
> **DougalLongfoot said:**
> I seem to have gotten my new installation over this bug (crosses fingers). All I did was update the BIOS to A32 and also went to System>Administration>Synaptic Package Manager. Once the package manager was open, did a quick search for i915, and reinstalled xserver-xorg-video-intel since then I haven't had the black screen on startup.

I was wondering if anyone could get anything happening in the System>Preferences>Display panel though. I open it, but there is nothing to see and I can't change any options.

Good to here you got it installed.:P

As far as the Display settings, it is at the best for the 1100 with this package.  All effects will work if you so choose.:lolflag:

shadetree

---

### Post by razielhamalach7 on 2009-09-20
How do you put BIOS A32 on without MS DOS?

---

### Post by shadetree1 on 2009-09-20
> **razielhamalach7 said:**
> How do you put BIOS A32 on without MS DOS?
 
Can you give us more information.  Do you have M$ installed?
 
shadetree

---

