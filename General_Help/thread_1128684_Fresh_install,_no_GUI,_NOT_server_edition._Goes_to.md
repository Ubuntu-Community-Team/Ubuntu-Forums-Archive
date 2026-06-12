---
title: "Fresh install, no GUI, NOT server edition. Goes to text login"
date: 2009-04-17
forum: General Help
---

### Post by Tsula on 2009-04-17
Okies, as it says, I've done 4 fresh installs of both Ubuntu 8.10 and 9.04 and after the install and updating, when I restart the computer, it goes text based for some reason instead of the GUI. Not sure what the issue is.. New to Linux. I've tried typing in startx and it says something about "No device/screen found" Confusing the hell outta me here. xD Any ideas guys and girls? xP

---

### Post by Mulenmar on 2009-04-17
You might not have a login manager installed. Try 

sudo apt-get install gdm

or

sudo apt-get install wdm

or 

sudo apt-get install kdm

EDIT: No device/screen found? Hmm...do you have the right drivers installed?

Post output of

lspci

in Terminal (Applications -> Accessories -> Terminal), and that might give a clue on what driver you need.

---

### Post by Tsula on 2009-04-17
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
01:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
02:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
02:02.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
04:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
05:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)


I'll be running the sudo's in a few minutes. Have to boot the system.

*EDIT* Ran the sudo for gdm -- It came up saying that it was already the newest version. So it's already installed.

---

### Post by Mulenmar on 2009-04-17
> **Tsula said:**
> 
03:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
04:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)

I'll be running the sudo's in a few minutes. Have to boot the system.

*EDIT* Ran the sudo for gdm -- It came up saying that it was already the newest version. So it's already installed.

So, you have two nVidia GeForce 9600 GTs...I don't know anything about running twin vid cards, but try the nVidia drivers.

I have no experience with nVidia cards, try [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by lykwydchykyn on 2009-04-17
Try this; it will install the nvidia drivers and configure them (at least, I think it should -- going on memory here):

```

sudo aptitude install nvidia-glx-180 nvidia-xconfig
sudo nvidia-xconfig
sudo reboot

```

---

### Post by Tsula on 2009-04-17
I checked out your link.. it has my issue in it but I don't understand how it can be done strictly from command lines...  

If you see multiple display cards listed, you need to explicitly add the PCI bus ID to your /etc/X11/xorg.conf file:

    *

      Use your text editor to open /etc/X11/xorg.conf. (try sudo vi /etc/X11/xorg.conf)
    *

      Find the line that says Section "Device"
    *

      Insert a new line that says BusID    "PCI:x:x:x", where x:x:x is the PCI address displayed by lshw command.
    *

      Save the file. If you had to restart into recovery mode, type reboot, otherwise restart your display using sudo /etc/init.d/gdm restart. 


Tried the commands there but it didn't let me edit it from Terminal on the live cd.

---

### Post by Tsula on 2009-04-17
> **lykwydchykyn said:**
> Try this; it will install the nvidia drivers and configure them (at least, I think it should -- going on memory here):

```

sudo aptitude install nvidia-glx-180 nvidia-xconfig
sudo nvidia-xconfig
sudo reboot

```

Trying that now.

---

### Post by Tsula on 2009-04-17
> **lykwydchykyn said:**
> Try this; it will install the nvidia drivers and configure them (at least, I think it should -- going on memory here):

```

sudo aptitude install nvidia-glx-180 nvidia-xconfig
sudo nvidia-xconfig
sudo reboot

```

It said it didn't recognise nvidia-xconfig so it didn't get any packages.

---

### Post by Mulenmar on 2009-04-17
These threads are about the same video card you seem to have, the nVidia GeForce 9600 GT.

[http://ubuntuforums.org/showthread.php?t=832505](http://ubuntuforums.org/showthread.php?t=832505)
[http://ubuntuforums.org/showthread.php?t=863205](http://ubuntuforums.org/showthread.php?t=863205)

---

### Post by Tsula on 2009-04-17
> **Mulenmar said:**
> These threads are about the same video card you seem to have, the nVidia GeForce 9600 GT.

[http://ubuntuforums.org/showthread.php?t=832505](http://ubuntuforums.org/showthread.php?t=832505)
[http://ubuntuforums.org/showthread.php?t=863205](http://ubuntuforums.org/showthread.php?t=863205)

Thanks, but nah, they didn't do anything for it.

---

### Post by lykwydchykyn on 2009-04-17
> **Tsula said:**
> It said it didn't recognise nvidia-xconfig so it didn't get any packages.

Ah, it appears to be in the universe repositories, which are not enabled by default.  It is just possible that installing nvidia-glx-180 is sufficient to get it working, but if not we can either manually enable the driver, or enable universe and install nvidia-xconfig.  

To enable universe:
 - open the file /etc/apt/sources.list using sudo:
```

sudo nano /etc/apt/sources.list

```
 - Remove the "#" mark from the beginning of the lines that say "universe" at the end (not counting the obvious comments).
 - Hit ctrl-x and 'y' to save and exit the editor.
 - Now do:
```

sudo aptitude update
sudo aptitude install nvidia-xconfig
sudo nvidia-xconfig
sudo reboot

```

---

### Post by Mulenmar on 2009-04-17
EDITED: Try lykwydchykyn's suggestion first, it's way less time-consuming.

When you installed, which disc (LiveCD, Alternate CD, DVD) did you use and what option did you pick? Maybe you accidentally selected a command-line install...

If nothing else works, maybe you could run

sudo apt-get purge xserver-xorg && sudo apt-get update && sudo aptitude install xorg envyng-core envyng-qt ubuntu-desktop

I'm pretty sure that will completely remove the graphics server and its configuration, then reinstall everything. It will also likely remove everything depending on it, which is why ubuntu-desktop is in the list.

If you want a Kubuntu or Xubuntu install, just replace ubuntu-desktop with kubuntu-desktop or xubuntu-desktop, respectively.

Maybe that'll do it. :popcorn:

---

### Post by Tsula on 2009-04-18
> **Mulenmar said:**
> EDITED: Try lykwydchykyn's suggestion first, it's way less time-consuming.

When you installed, which disc (LiveCD, Alternate CD, DVD) did you use and what option did you pick? Maybe you accidentally selected a command-line install...

If nothing else works, maybe you could run

sudo apt-get purge xserver-xorg && sudo apt-get update && sudo aptitude install xorg envyng-core envyng-qt ubuntu-desktop

I'm pretty sure that will completely remove the graphics server and its configuration, then reinstall everything. It will also likely remove everything depending on it, which is why ubuntu-desktop is in the list.

If you want a Kubuntu or Xubuntu install, just replace ubuntu-desktop with kubuntu-desktop or xubuntu-desktop, respectively.

Maybe that'll do it. :popcorn:

It's the LiveCD. That why I'm able to get on the net atm. I ran into a different issue now. I tried to reboot again back to the HD instead of the LiveCD and now it's not going command line anymore.. It goes to something called Busybox.

---

### Post by Mulenmar on 2009-04-18
Busybox? That's still a command-line, isn't it? Or is there graphics?

---

### Post by Tsula on 2009-04-18
It's a command-line, but sudo isn't recognised as a command..

---

### Post by Mulenmar on 2009-04-18
Is the end of the prompt a # or a $

# means you're already root. Be careful.

---

### Post by Tsula on 2009-04-18
Neither. It just gives (initramfs).

---

### Post by Mulenmar on 2009-04-18
:o I can't help you from there, then. I haven't delved THAT deep into that part.

I really hate to say it, but you'll either have to reinstall or do some slightly complicated things from on the LiveCD. 

Unless someone else knows a way to fix that.

---

### Post by Tsula on 2009-04-18
Heh, Okies, thanks xD

---

### Post by Yashiro on 2009-04-18
If you're running two video cards, pull one out.
Re-install. Do NOT install the 'restricted drivers' if it pops up.

There's either a driver issue or you're making the same error every time you install.

---

### Post by Tsula on 2009-04-18
So I couldn't do two cards until I figure out how to configure it correctly?

---

### Post by Yashiro on 2009-04-18
It's basic troubleshooting practice.

If Ubuntu gets installed,
you get the Nvidia restricted/proprietary drivers setup,
and reboot succesfully, 
then put the second card in.

---

