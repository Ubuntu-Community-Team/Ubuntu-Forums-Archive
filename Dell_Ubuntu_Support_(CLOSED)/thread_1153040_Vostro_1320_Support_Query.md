---
title: "Vostro 1320 Support Query"
date: 2009-05-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wfitzgerald on 2009-05-08
Hi,

Has anyone had any experience of Ubuntu 9.04 0r 8.04 on a dell Vostro 1320 model?

I will pretty much keep (on purchase) the dell offered defaults for example:
IntelCore2 Duo Processor P8600 (2.4GHz, 1066MHz FSB,3MB L2 cache), 256 MB NVIDIA, 8GB RAM, standard wireless ab/g card.

regards,
Will.

---

### Post by coffeeaddict22 on 2009-05-08
You could always wander into the shop with a Live CD.  If anything's going to play up it'll show up (if they let you run it).  

The problem is that you need to know the chipsets to decide, and the stuff on the outside of the box doesn't tell you that.  Dell does sell a few Linux setups- if you live in the right country and search their website hard enough- but (like the rest of us) at times they seem to have problems with the hardware not getting as good support as you'd like.  The Intel video driver is a case in point at the moment.  At a guess, NVIDIA should be fine, the motherboard won't be an issue, the wireless could be, and the soundcard might be.

---

### Post by wfitzgerald on 2009-05-09
> **coffeeaddict22 said:**
> You could always wander into the shop with a Live CD.  If anything's going to play up it'll show up (if they let you run it).  

The problem is that you need to know the chipsets to decide, and the stuff on the outside of the box doesn't tell you that.  Dell does sell a few Linux setups- if you live in the right country and search their website hard enough- but (like the rest of us) at times they seem to have problems with the hardware not getting as good support as you'd like.  The Intel video driver is a case in point at the moment.  At a guess, NVIDIA should be fine, the motherboard won't be an issue, the wireless could be, and the soundcard might be.

Thanks. Still waiting on Dell to call me back. Dell ship (some) machines with Ubuntu installed. But there was not an option on this model as with about 90% of their products.

---

### Post by TheDogDidIt on 2009-05-14
My Vostro 1320 just arrived.  Same specs as mentioned above except I got mine with 2GB RAM instead of 8GB.  It's cheaper to get the RAM from a third party than through Dell.

I was pleasantly surprised to find that the sound, wireless and video worked without a hitch.

I worked through the Vista installation and then split the drive (for dual booting) using the disk management utility and installed Ubuntu 9.04 with the alternate installer.  I did not have a network connection so everything was installed from the CD.

Booting to the desktop I had sound.  Cool.  The hardware driver utility told me it was using a proprietary Broadcom driver.  I clicked the wireless tool, found my AP and connected to it without a problem.  I ran the Update Manager, rebooted and reran the hardware driver utility and it suggested that I install the Nvidia driver for the video card.  I installed it, rebooted and have hardware accelerated video.  Excellent.

I have not played with power management features or with the Ethernet NIC.

I hope this helps.

Edit:  I got the standard b/g card - not ab/g (don't think that was offered) or a/g/n.

---

### Post by wfitzgerald on 2009-05-25
thanks TheDogDidIt ;-)

Yea, I was going to go for the standard wireless card to be on the safe side rather than the new N-standard.

Sorry for the late reply.
Cheers,
Will.

---

### Post by simplysped on 2009-05-29
I just got my Vostro 1320 and I installed the newest Ubuntu. For some reason when I start the keyboard and trackpad don't work unless the power is plugged in. Anyone have this problem?

---

### Post by wfitzgerald on 2009-05-29
> **simplysped said:**
> I just got my Vostro 1320 and I installed the newest Ubuntu. For some reason when I start the keyboard and trackpad don't work unless the power is plugged in. Anyone have this problem?

I just put my order in today for the Vostro. It will be at least 3 weeks before I get mine to confirm if I get the same result as you. 

I presumed keyboard drivers etc where pretty nailed down. 

You might need to look at your "xorg.conf" file and reconfigure using dpkg-reconfigure xerver-xorg.

I am no expert here, though.

---

### Post by simplysped on 2009-05-29
> **wfitzgerald said:**
> I just put my order in today for the Vostro. It will be at least 3 weeks before I get mine to confirm if I get the same result as you. 

I presumed keyboard drivers etc where pretty nailed down. 

You might need to look at your "xorg.conf" file and reconfigure using dpkg-reconfigure xerver-xorg.

I am no expert here, though.

big noob here, is that a terminal command?

---

### Post by wfitzgerald on 2009-05-30
yes, its a command for the terminal. Perhaps stay away from editing system files for now. Google is your friend here for example "Ubuntu Xorg keyboard stops".

the Xorg file is in folder /etc/x11. 
#If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"ie"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection



A few things to try:

(1) You could try the following keys to restart the X server:
Ctrl-Alt-Backspace key combination

Does your keyboard work now?

(2) I wonder has it to do with the power manager. To install new software go to: System --> Administration --> Synaptic Package Manager 

now search to make sure you have the "Synaptics TouchPad driver for X.Org server" installed (that is it has a green box beside it).

Search to see if you have acpid installed.

I am sure you have all the above. So you may have to take option (3).

(3) Download a new copy of Ubuntu in case the previous one you used was not a 100%. Do a new install.

---

### Post by fca_neo on 2009-08-01
Some notes on my own experience:

I have a Vostro 1320 with 4GB of RAM, Wireless adaptor n, G Force 9300M GS.I'm using Kubuntu Jaunty.

I have a similar issue with the keyboard ans touchpad. If the computer is shut down and I start it up, the touchpad and keyboard are not functional. The only way to interact with the computer is trough external peripherals. As soon as I restart it (or when resuming from "suspend to disk"), the touchpad and keyboard work very well. This is independent of the power cord being plugged in.

Also, the sound is not very loud (which might be normal considering it has only a single speaker) and when I connect headphones the speaker remains functional (i.e. the sound from the speaker does not stop when plugging headphones).

Furthermore, the built in microphone is not listed in the sound capture channels.

Besides that everything works very well and it is a nicely built and powerful computer.

I would like to solve the audio problems, and the keyboard and touchpad problem, but I don't really know what causes them and thus how to tackle them.

Thanks for any tips on how to solve these problems and on what causes them.

---

### Post by volrath2 on 2009-08-02
Hi, I've got the same problem: on my vostro 1320 i can't use built-in keyboard and mouse. I've tried ubuntu 9.04 x64, 8.10 x64. Now i can't try to reconfigure x-server, (now i'm on vostro 1400 with no problems) but  i'll say you the result as soon as possible running a terminal in live mode before the install. 

Do you think we have to try with 32 bit distributions? It' a strange problem, all the other hardware works fine.

 If helpful i tried the windows 7 rc on the same notebook and sometimes touchpad doesn't work, it works fine only using Vista Businnes :(  

but i want't to use ubuntu!

---

### Post by eligos on 2009-08-02
For the keyboard/touchpad problem, you need to add the following boot parameters to the file /boot/grub/menu.lst in the kernel line

```
i8042.nomux i8042.nopnp i8042.noloop 
```

Example:

```
kernel		/boot/vmlinuz-2.6.28-15-server root=UUID=abbd29e5-77f8-47d9-a640-57727c441a95 ro quiet splash i8042.reset i8042.nomux i8042.nopnp i8042.noloop
```

---

### Post by volrath666 on 2009-08-03
Thanks !

---

### Post by wfitzgerald on 2009-08-06
> **fca_neo said:**
> Some notes on my own experience:

I have a Vostro 1320 with 4GB of RAM, Wireless adaptor n, G Force 9300M GS.I'm using Kubuntu Jaunty.

I have a similar issue with the keyboard ans touchpad. If the computer is shut down and I start it up, the touchpad and keyboard are not functional. The only way to interact with the computer is trough external peripherals. As soon as I restart it (or when resuming from "suspend to disk"), the touchpad and keyboard work very well. This is independent of the power cord being plugged in.

Also, the sound is not very loud (which might be normal considering it has only a single speaker) and when I connect headphones the speaker remains functional (i.e. the sound from the speaker does not stop when plugging headphones).


Furthermore, the built in microphone is not listed in the sound capture channels.

Besides that everything works very well and it is a nicely built and powerful computer.

I would like to solve the audio problems, and the keyboard and touchpad problem, but I don't really know what causes them and thus how to tackle them.

Thanks for any tips on how to solve these problems and on what causes them.

Apologies for not getting back to you sooner. In the end, I went for a latitude E4300. Its supposed to be a more robust version of the Vostro.

With the Latitude E4300 I have had no issues with the Keyboard and Touchpad. I had a little trouble configuring the dual screen xorg setup but is has not been ironed out.

I agree the Sound is terrible. The volume, has to be turned up at least 3/4 before any sound is heard! Also, I am still having trouble configuring my Mic for Skype or for the Sound Recorder (under the Sound & Video application list).

Another note I would like to make is that, my laptop is supposed to have 4GB RAM and 250GB hard-drive. However, Ubuntu 9.04 only sees 3.5GB of RAM and 220GB of hard-drive!

cheers,
Will.

---

### Post by fca_neo on 2009-08-26
> **eligos said:**
> For the keyboard/touchpad problem, you need to add the following boot parameters to the file /boot/grub/menu.lst in the kernel line

```
i8042.nomux i8042.nopnp i8042.noloop 
```

Example:

```
kernel		/boot/vmlinuz-2.6.28-15-server root=UUID=abbd29e5-77f8-47d9-a640-57727c441a95 ro quiet splash i8042.reset i8042.nomux i8042.nopnp i8042.noloop
```

Thank you for the reply, your solution works very well. although it is important to note that

```
i8042.reset i8042.nomux i8042.nopnp i8042.noloop
```

is the string to be appended, as you show in your example.

Also, anybody knows what this option actually does? I'm curious to see what is the change between a fresh start as opposed to a resume form disk or restart.

Cheers and thanks to all for the feedback.

On problem down!:)

---

### Post by volrath2 on 2009-09-15
Hi, I don't know exactly if the problem is this:

After I tried to add the suggested line to menu.lst my votro 1320 works fine, but sometimes, when unplugged form AC, the touchpead doesn't work again :(

I searched over the internet and i found that the problem may be the UBS CORE AUTOSUSPEND: the kernel turn of the usb core and the mouse (connected to the same BUS ??) when unused.

Infact, a reboot with a usb pen plugged in makes the touchped alive.

In Ubuntu 9.04 you can't disable the kernel module USBCORE.AUTOSUSPEND=-1 in menu.lst (-1 means "always turned OFF") .. so you have tu add this option to a .conf file in /etc/modprobe.d/ ore you should compile a new kernel without this module.

I tried to add the option to modprobe.d but nothing happens :(

I'm not shure of this!!

---

### Post by fca_neo on 2009-09-16
I solved the sound problem!

Now, the sound works flawlessly. I can even use Skype without any troubles.

In order to fix it I installed the new Alsa by following the instructions here: [http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/]("http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/")

The guide is very complete and easy to follow. Also, you could try installing the 1.0.21 version since it is newer and may work fine too. I installed the 1.0.20 version since I did not realize that a newer one was out.

I hope this helps. Cheers!

---

### Post by charding on 2010-01-03
I'm glad I found the problems and solutions to these problems.

I'm thinking about getting this laptop. 

I read on the dell ubuntu community support site that there may be problems with the wireless 1510 card or the 1397 that is also shipped with this laptop. This may be when you install 9.10 but 9.04 works out of the box.

I read that for 9.10 the 1397 wireless card uses the Broadcom 4312 driver and the 1510 card using the sta driver (wl module) that can be downloaded from the broadcom site.

---

