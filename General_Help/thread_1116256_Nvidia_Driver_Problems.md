---
title: "Nvidia Driver Problems"
date: 2009-04-04
forum: General Help
---

### Post by jixtersnoop on 2009-04-04
Ubuntu 8.10
Nvidia 9800 Gtx+
Problem: Unable to use Nvidia drivers

Alright, I am about at my wits end on this one. I am new to linux and have been working through it for a few days now, and in these endeavors I noticed my drivers on Nvidia were not enabled. Basically, every time I got the drivers installed, when I reboot, I get an error and am forced to start in low graphics mode. I have gone through 6-8 different topics with a couple solutions each to this problem, but like many people in these topics, I was still unable to resolve these issues. I have found it is beyond me to solve this, so I am hoping someone can help me track down the issue. As things stand, here are the last things I have done, and the error that resulted from them

1) Reinstalled Ubuntu 8.10
2) Installed Updates and rebooted
3) Downloaded the Nvidia-Linux x86 180.44 driver to desktop
4) Hit Ctrl+Alt+F1 to bring up the terminal by itself, and ran the      following commands:
       a) sudo killall gdm
       b) cd Desktop
       c) sudo sh ./NVIDIA-Linux-x86-180.44-pkg1.run
       d) Selected "yes" to every question in the installation
5) I then rebooted, and was confronted with the following errors
(EE) Failed to load module "type1" (module does not exist, 0)
(EE) NVIDIA(0): Failed to initialize the nvidia graphics device PCI:1:0:0 
(EE) Screen(s) found, but none have a usable configuration.

I then have to run in low graphics mode, and additionally when I try to run the NVIDIA X Server Settings, I get the error
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

Like I said, I have tried most solutions, but I may have made a mistake in trying to follow them, so I am willing to start from square one on this one. Thanks in advance for the help :)

---

### Post by coffeecat on 2009-04-04
Rather than download the nvidia driver and compile it yourself, did you try the inbuilt Ubuntu way? Which is the recommended method. System > Adminstration > Hardware Drivers. Tick the box for the recommended nvidia driver. Let the system autoinstall the pre-prepared packages. Reboot.

---

### Post by jixtersnoop on 2009-04-04
Will try that now, (the recommended driver is 177). I also noticed when I went to do this, the driver that I was told successfully installed (the 180 one) was not listed here. Ill update with what happens after I try installing this one.

---

### Post by jixtersnoop on 2009-04-04
Ok, I tried using the built in installer, and was still presented with the exact same error and issues. However, unlike the 180 driver, this one appears in the Hardware Drivers list, and is now showing being activated. But beyond this, I am still stuck in low graphics mode and with the error.

---

### Post by coffeecat on 2009-04-04
Have you checked System > Preferences > Display? If that doesn't help, it's possible the problem is with your monitor. Some don't put out reliable EDID data, and this confuses the xserver. If this is the case it may be possible to get around this by doing a manual edit of your /etc/X11/xorg.conf file.

But I'm afraid I'll have to log off now - it's very late here - so I can't follow you with this. At least not for a few hours.

---

### Post by jixtersnoop on 2009-04-04
I don't have a Display option under System->Preferences. Thanks for trying. Anyone else have a viable solution, or know where to pick up where coffee left off?

---

### Post by Sylslay on 2009-04-04
To coffecat. 
What meant :No proprietary drivers are in use on this system.
Checked /system/Administration/HardwereDrives

Should be something to thick?
PS// Not native English

---

### Post by jixtersnoop on 2009-04-04
In delving for other threads I may of missed on this topic, I came across something that did manage to remove the '(EE) Failed to load module "type1" (module does not exist, 0)' line of my error. It said to add 'vmalloc=192M pci=nommconf' to the /boot/grub/menu.lst on the kernel line. However, the rest of the error, and all the problems that come with it, are still present

---

### Post by norwoods on 2009-04-04
i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.44 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  
first run:
sudo nvidia-installer --uninstall
sudo apt-get install build-essential linux-headers-`uname -r`

then use synaptic to install, i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig
open System-->Administration-->Hardware Drivers.
if there is an active video driver, click on it and then click Deactivate
click on the NVIDIA 180 driver
click Activate.
clock Close.
reboot

---

### Post by jixtersnoop on 2009-04-04
Ok, now I at least see the 180.44 driver being activated in the hardware drivers section, just like the 177 one was before, but the error and the state of being stuck in low graphics mode has not changed. I had a little difficulty understanding what you said to do, so just to recap to make sure we are the same page....

I ran
sudo nvidia-installer --uninstall
sudo apt-get install build-essential linux-headers-`uname -r`

Installed
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
all from that website repos address

and before installing these 6 things, made sure I had
jockey-common
jockey-gtk 
nvidia-settings
nvidia-xconfig

At this point the 180 driver was present and activated, however as I said the actual issues at hand are still present.

---

### Post by norwoods on 2009-04-04
can you run:
gksu nvidia-settings
and see if there is any way to fix things?

---

### Post by jixtersnoop on 2009-04-04
> **norwoods said:**
> can you run:
gksu nvidia-settings
and see if there is any way to fix things?

I ran it, and I got the error

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

Also, I don't know if that matters, but I am running a 32 bit Ubuntu, not 64

Also, when trying to run nvidia-xconfig, I get:

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: No Layout specified, constructing implicit layout section using screen
         "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add new
         CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new
         CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

---

### Post by jixtersnoop on 2009-04-05
Another update. I found a program called compiz-check that will scan your system to see if compiz could run, and if it couldn't, why that is the case. Here is what the program outputted:

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 9800 GTX (rev a2)
 Driver in use:         vesa
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

This surpised me, since right now my hardware drivers page shows that the 180 drivers are activated, yet this only detects the vesa ones.

Edit: In an attempt to simplify the problem and track down where it is occuring, I did the following.
1) Reinstalled Ubuntu
2) Activated the recommened 1.77 driver *without* getting updates
3) All errors still occur

In otherwords, with doing the bare basics from a fresh install, it still does not work.

---

### Post by omgseth on 2009-04-05
This post helped me with my Nvidia 9500, maybe it could help you as well?

[http://ubuntuforums.org/showthread.php?t=925309](http://ubuntuforums.org/showthread.php?t=925309)

---

### Post by coffeecat on 2009-04-05
Here's something very odd, and something I've never seen before on systems I've used with various nvidia graphics chipsets:

> **jixtersnoop said:**
> Driver in use:         vesa

Whenever I've installed Ubuntu on a system with nvidia, the installer has set me up with the 'nv' driver - that's the open source driver for nvidia. And then the transition to the proprietary 'nvidia' driver has been easy.

The 'vesa' driver is the most basic of xserver drivers which will work on all graphics cards. I wonder if it's the fact that the vesa driver has been set up rather than nv that's causing a failure of nvidia install. I don't see why it should, but who knows? :? Also, possibly the reason for the low resolution, although I thought the vesa driver could go up to 1024x768, possibly 1280x1024. By the way, what's the resolution of your monitor? And any idea of the resolution you were getting? I know you didn't have a GUI way of telling you but some flat screen monitors can tell you from their config menus what signal is coming in.

First, we need to see if there is anything about your hardware that's confusing the installer. Post the terminal output of:

```
lspci
```Another possibility is that if you have both an onboard graphics card and a separate PCIe/AGP graphics card, something in the BIOS setting is confusing the installer and/or the nvidia installer.

Second, have a look in /etc/X11/xorg.conf. That's the xserver configuration file, where your graphics driver gets defined. Look for the Device section and, in that, the line:

```
Driver    "vesa"
```You could try this following but, be warned, if you make an errror or if there's a more obscure fundamental problem, editing xorg.conf can lead to the xserver failing so that you get dumped into a console on bootup. From a terminal:

```
gksudo gedit /etc/X11/xorg.conf
```and then change that driver line to:

```
     Driver   "nv"
```Save, exit and reboot and you should be seeing the display using the nv driver. Hopefully, that should fix the resolution problem, but won't give you hardware acceleration. Now try reinstalling the nvidia driver whichever way you prefer. I don't advise editing xorg.conf to read 'Driver "nvidia" ' in one go. If the proprietary nvidia driver has been properly compiled and installed that will work, but we can't be sure that's the case.

**Edit:** another possibility is that there's no driver line in your xorg.conf and the system is defaulting back to the vesa driver. If this is the case, post the whole of your xorg.conf file (it's not big) and we'll take it from there. I've got visitors coming in a couple of hours time. I'll check this thread just before, but then I won't be able to come back for about 8 hours. I hope we can fix this.

---

### Post by norwoods on 2009-04-05
the nvidia 185.13 driver is now in the intrepid main repository.
how about a fresh install, update and add the new driver.

---

### Post by jixtersnoop on 2009-04-05
I tried envyng, but to no avail (ended up with the same result as installing manually).

I should probably point out that when you asked earlier for System->Preferences->Display, I saw that I did have System->Preferences->Appearence, which may of been what you meant. Regardless I can just go to System->Preferences->Screen Resolution to see my options, and I am set to my default max at 1680x1050, so there are no problems there. I did notice, oddly enough, my refresh rate can only be set to 0Hz, and there are no other options present. Also, the monitor is "unknown".

lspci gave me:

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GTX (rev a2)
02:01.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
02:04.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
02:05.0 Ethernet controller: Atheros Communications Inc. AR5413 802.11abg NIC (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)

The xorg file contained this plus commented code above it:

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option	"NoLogo"	"True"
	Driver	"nvidia"
EndSection

Also, is it possible it is defaulting to vesa since I am in low graphics mode? Anyway, even though the xorg says it is trying to load nvidia, I'll see what happens when I change it to nv, just to see what happens. After that, I'll try what norwoods says and post my results

Edit: I was able to boot normally using the nv driver without error, but I assume this much was expected. I double checked with compiz-check, and it confirmed the driver currently active was the nv one. I tried at this point to switch to my latest installed nvidia driver, but it said I had to restart for it to function. Anyhow, time for a fresh install and trying norwoods idea...

---

### Post by jixtersnoop on 2009-04-05
And....no dice. Fresh reinstall with updates, activated 180 and restarted, same results. :-/

---

### Post by norwoods on 2009-04-05
is nVidia Corporation GeForce 9800 GTX (rev a2) a dual gpu card?
nvidia has a README for each driver version, see the following for 185.13 32 bit:
[ftp://download.nvidia.com/XFree86/Linux-x86/185.13/README/index.html](ftp://download.nvidia.com/XFree86/Linux-x86/185.13/README/index.html)

---

### Post by wrose51106 on 2009-04-05
Let me try to help, I am by no means a Linux guru, for I have just started tinkering a few days ago; but have learned a lot so far.

I just did this a few hours back, head into package manager, search Nvidia, uncheck everything referencing Nvidia. Reboot, log in clicking defaults.

Head back into package manager, check the Nvidia-glx-180-dev, it will grab a few dependencies with er, install reboot and you should be good to go.

-Bill

---

### Post by jixtersnoop on 2009-04-05
I went through the readme but didn't see anything that would help. I also tried what you suggested wrose, but it was the same old error

---

### Post by coffeecat on 2009-04-05
Sorry I haven't got back earlier but I've been completely perplexed by the fact that compiz-check is telling you that you are running the vesa driver (which is why I said xorg.conf would show vesa) whereas when you went into xorg.conf it was configured for the nvidia driver. I think this is a case for some emoticons: :-k  ](*,) :-( .

I am really beginning to wonder if there is an obscure hardware issue confusing the xserver. I noticed something interesting in lspci:

> **jixtersnoop said:**
> 01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GTX (rev a2)
02:01.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
02:04.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder

Your nvidia card is there, but also some sort of video device - the Conexant. What is that?

---

### Post by jixtersnoop on 2009-04-05
I'm not 100% positive, but I think that is my tv capture card.

---

### Post by coffeecat on 2009-04-05
Hmmm. Interesting.

[This thread]("http://ubuntuforums.org/showthread.php?t=965180") is not directly relevant to your problem, but it may contain a clue. The thread is about a 8.10 problem where people who have two nvidia graphics chipsets (usually onboard and a separate card) and who install the proprietary nvidia driver get a complete failure of the xserver. There are several posted fixes but, as I said, not relevant to you. However, there's a poster somewhere in the middle who found that his TV card was interfering - iirc. He removed the TV card and the nvidia problem went away.

I have two PCs, both with two nvidia graphics devices, onboard and separate cards (all different chipsets). In one I didn't get this issue. In the one with the Hauppage TV card I did. Unfortunately for me none of the posted fixes worked, and as this machine was my TV recording machine taking the TV card out wasn't an option. :( So in this one I removed the PCIe card, and now all is well in Intrepid.

But again, different problem to yours. However, it does seems as if a TV card with a nvidia graphics card can be an issue. Obviously an obscure one. The reason I'm saying all this is that it might be worth temporarily removing the TV card and trying over. If you can successfully install the nvidia driver, at least you'll know what the problem is, even if that leaves you with an invidious choice.

---

### Post by jixtersnoop on 2009-04-05
Alright. I don't have the tools on hand to remove it, but once I do I'll take it out, try again, and post the results.

---

### Post by jixtersnoop on 2009-04-08
> **jixtersnoop said:**
> Alright. I don't have the tools on hand to remove it, but once I do I'll take it out, try again, and post the results.

Sweet victory! It turns out it was the tv card after all. I would go straight into trying to get it working with the card, but I am so happy to finally be able to try out some of the desktop effects I have seen, I think I will wait alittle while. Many thanks to everyone who helped, especially coffeecat :guitar: 

You will probably see me with a new thread in a week or so starting from using the tv card.

---

### Post by coffeecat on 2009-04-09
I'm really glad it's sorted.

> **jixtersnoop said:**
> You will probably see me with a new thread in a week or so starting from using the tv card.

Well, here's a few thoughts for you in the interim. You remember that machine I told you about, the one with two nvidia graphics devices and the Hauppage TV card? And I had to take out the nvidia PCIe card to get Intrepid to behave with the nvidia proprietary driver? Well, I've tried it with Jaunty Beta, and Jaunty tolerates having both the PCIe card and the TV card in at the same time when it uses the proprietary driver. Hooray! Trouble is, although both Hardy and Intrepid detect the TV card, Jaunty doesn't. :(  ](*,)

Of course, your TV card probably has a different chipset from mine, so you may be OK when you come to use Jaunty. However.....

I have a laptop with which I use a Hauppage USB TV device. It works fine with Hardy and Intrepid. Jaunty seems to detect that OK, but the Jaunty version of me-tv doesn't wat to play ball with it.  :cry: 

Ah well, fun and games! :-\"

Anyway, despite all that you might want to consider getting a USB TV card. But do research the compatibility of the chipset first. :wink:

---

### Post by practic on 2009-04-30
I just ran into a similar problem installing Jaunty on a new computer with an nVidia 8400GS in the PCIe slot.  Everything installed and worked great, and then I decided to add a TV card.  The one that gave me trouble was the Hauppauge WinTV-HVR-1600.  As soon as it was the system wouldn't boot clean to the desktop. Instead I got errors like:

"failed to initialize NVIDIA graphics device PCI:2:0:0"

I tried various things to resolve the error (reconfigure xserver, uninstall and reinstall nvidia drivers, use envy to install the drivers), nothing worked.  It seems to me like the reference to "PCI:2" in the above error indicates that it was trying to use the TV card instead of the graphics card.

I have a few other computers running Ubuntu 8.10 that have TV cards and nVidia cards and are working fine, although they are different brand TV cards, and they were in when the system was installed, so I'm not sure if that makes a difference.  I'm going to do a bit more testing to find out.

---

