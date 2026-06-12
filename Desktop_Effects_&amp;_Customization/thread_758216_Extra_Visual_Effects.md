---
title: "Extra Visual Effects"
date: 2008-04-17
forum: Desktop Effects &amp; Customization
---

### Post by .adma on 2008-04-17
Hi all, for some reason when I go to enable the advanced effects under visual effects I get the warning:

"Desktop Effects Could not be Enabled"

I will give you a bunch of information about my system below to help with troubleshooting.  My 3d Graphics card (Radeon 7500) appears to be working perfectly, so I don't know what the deal is...

```
lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

```

```
 sudo lshw -C video
[sudo] password for adam: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Radeon Mobility M7 LW [Radeon Mobility 7500]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
       configuration: latency=66 mingnt=8
adam@adam-laptop:~$ sudo lshw -C video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Radeon Mobility M7 LW [Radeon Mobility 7500]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
       configuration: latency=66 mingnt=8
adam@adam-laptop:~$ glxinfo | grep -i direct
direct rendering: Yes
adam@adam-laptop:~$ glxinfo | grep -i opengl
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:

```

And with glxgears I get: 700 FPS.  Any suggestions???  Thanks!!

---

### Post by .adma on 2008-04-18
Out of all you geniuses, there are no takers to my seemingly easy problem?  Thanks!

---

### Post by Juhla Mokka on 2008-04-19
I would like to know too. I've got almost brand new laptop that should be able to handle them.

---

### Post by Zorael on 2008-04-19
Uh, display unclaimed doesn't sound very good. What is the output of entering the following in a terminal?

```
$ compiz --replace &
```

Enter '**metacity --replace &**' to revert if things turn ugly.

---

### Post by Juhla Mokka on 2008-04-19
Hi, just to let you know that I got them working by following afterburn's advice top of this page [http://ubuntuforums.org/showthread.php?t=582207&page=2](http://ubuntuforums.org/showthread.php?t=582207&page=2)

Happy :)

---

### Post by .adma on 2008-04-19
> **Zorael said:**
> Uh, display unclaimed doesn't sound very good. What is the output of entering the following in a terminal?

```
$ compiz --replace &
```

Enter '**metacity --replace &**' to revert if things turn ugly.

```
~$ compiz --replace &
Checking for Xgl: [1] 24944
adam@adam-laptop:~$ not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity
```

---

### Post by Zorael on 2008-04-19
I don't know enough about ATI drivers to make more than educated guesses, but if I were you, I'd try running Envy and see what it installed for me. I'm a bit lost when it comes to mesa, fglrx and all that. *IF* you don't like the changes Envy made, run it again and have it remove all installed drivers, then reconfigure xorg; **sudo dpkg-reconfigure xserver-xorg**. That'll restore your X server settings (input and video devices) to defaults. If you can only boot up into safe graphics mode, that's not the end of the world, we'll just need to take a look at some logs.

One solution would be to install xserver-xgl, yes. Might help but things'd be mighty slow. It's a big no-no for Nvidia and standard ATI cards though, so I'd try Envy first.
edit: But remember, these are educated guesses, perhaps your Mobility chipset just happens to need xgl to do anything at all.

Before doing anything, make a backup copy of your xorg file. (**/etc/X11/xorg.conf**)

Then [get Envy here.](http://albertomilone.com/nvidia_scripts1.html)


If things go bad and you want help troubleshooting, we'll want to see the contents of said xorg.conf as well as your **/var/log/Xorg.0.log** files.

---

### Post by .adma on 2008-04-19
> **Zorael said:**
> I don't know enough about ATI drivers to make more than educated guesses, but if I were you, I'd try running Envy and see what it installed for me. I'm a bit lost when it comes to mesa, fglrx and all that. *IF* you don't like the changes Envy made, run it again and have it remove all installed drivers, then reconfigure xorg; **sudo dpkg-reconfigure xserver-xorg**. That'll restore your X server settings (input and video devices) to defaults. If you can only boot up into safe graphics mode, that's not the end of the world, we'll just need to take a look at some logs.

One solution would be to install xserver-xgl, yes. Might help but things'd be mighty slow. It's a big no-no for Nvidia and standard ATI cards though, so I'd try Envy first.
edit: But remember, these are educated guesses, perhaps your Mobility chipset just happens to need xgl to do anything at all.

Before doing anything, make a backup copy of your xorg file. (**/etc/X11/xorg.conf**)

Then [get Envy here.](http://albertomilone.com/nvidia_scripts1.html)


If things go bad and you want help troubleshooting, we'll want to see the contents of said xorg.conf as well as your **/var/log/Xorg.0.log** files.

Thanks for the help!  I did try xserver-glx,  It made the special effects work, but it was insanely (and unbearably slow).  I will give envy a shot soon.  Thanks for your help, this is great!

---

