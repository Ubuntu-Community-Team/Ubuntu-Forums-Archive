---
title: "Neverwinter Nights Visual Problems"
date: 2012-06-18
forum: Gaming &amp; Leisure
---

### Post by Sanus Compleo on 2012-06-18
VGA: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller
Ubuntu 12.04, 64-bit running well above the recommended requirements for Neverwinter Nights.  (Output of lspci included below body of post)
Hak Packs included: CEP2.4, PRC3.5

So I just get through installing Neverwinter Nights (Twice, once with Wine and then with native client) and installed CEP and PRC and everything shiny, update with Critical Rebuild (Once with wine, once with native) and... 

[http://i.imgur.com/ln7j5.jpg](http://i.imgur.com/ln7j5.jpg)

What fresh hell?

Let's do a rundown of the problems here, shall we?

Firstly, there's the big black... -things- that are appearing everywhere.  Messing around with the camera angle seems to randomly generate more, as well as causing already existing ones to flicker - and most of the time they fill up the whole screen (I just moved it around until I got one that allowed me to see a good deal of the screen.)

Second, we've got lil' miss No-Torso, which is bizarre, and in the back we have Mr. No-arms.  Okay, not to mention the complete stark white textured table in the background.  (The last I'm used to, the stark texture?  It's related to having old drivers for your video card, because of a compressed texture type or some such stuff.  Every install of Nwn I've ever played has had that same problem.)  The same thing happens in native (This was taken with the wine install)

I'm at my wit's end, really.  It's taken me all day just to get this far, and rummaging throughout the entire internet so far has just told me that nobody else has ever seemed to have this issue.  So I'm really... really stuck.

If it's important, Mr. No-arms was wearing some kind of cloak/jacket.  I'm not sure what Miss No-Torso was wearing.  Robes seem to trigger the graphics glitching as well.

Get ready for lspci output!  (Is there some way to spoiler this?)

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

```

---

### Post by Sanus Compleo on 2012-06-19
Thanks to Skildron of the Bioware NWN community, I learned that enabling ST3C via driconf enabled me to see the tables and cabinets and other white textures that were previously compressed and impossible to see.

The black objects are still everywhere.  Everywhere.

---

### Post by Skildron on 2012-06-19
To disable kernel mode setting, you need to edit the file /etc/default/grub

sudo <favourite_editor> /etc/default/grub

Add the keyword 'nomodeset' to the line starting with
GRUB_CMDLINE_LINUX_DEFAULT=
of course, within the quotation marks.

Next, you have to update your boot manager:

sudo update-grub

Next step: reboot

I hope this helps, there have been lots of complaints in the past that NWN does not work well with kernel mode setting (KMS) enabled - but disabling it has its downsides, too. You will lose the graphical splash screen on bootup and the start of the graphical login manager will take some seconds longer - that way, adding to boot time. You can try if it helps, if not, you can always take the change back.

Greetings
Skildron

---

### Post by jemino on 2012-06-19
I had the same problem with the invisible bodies when robes or cloaks where equipped (using a Sandy Bridge GPU). I seem to have solved it by disabling the GL_NV_vertex_program OpenGL extension.

The best way to do this should be to set the MESA_EXTENSION_OVERRIDE environment variable before launching nwn. Edit the nwn script and add the following line before the "./nwmain $@" command :

```

...
export MESA_EXTENSION_OVERRIDE=-GL_NV_vertex_program
./nwmain $@

```Unfortunately, this didn't work for me (you should still try it before going with the next method).

I had to use the extension filter library (the original author doesn't seem to have any web presence). Download the attached file, unpack it and compile the library :

```

tar zxvf filter_ext-0.9.2.tar.gz
cd filter_ext
make
(note the message about the LD_PRELOAD variable)

```Since you're running a 64 bits system, you will need to install the needed tools and libs for cross-compiling to 32 bits :

```

sudo apt-get install gcc-multilib

```When you're done compiling, edit the nwn script and add the following lines before the "./nwmain $@" command :

```

...
export FILTER_EXT=GL_NV_vertex_program
export LD_PRELOAD=what-you-were-told-when-compiling-the-library
./nwmain $@

```I hope it will work for you too.

---

### Post by Sanus Compleo on 2012-06-19
> **jemino said:**
> I had the same problem with the invisible bodies when robes or cloaks where equipped (using a Sandy Bridge GPU). I seem to have solved it by disabling the GL_NV_vertex_program OpenGL extension.

The best way to do this should be to set the MESA_EXTENSION_OVERRIDE environment variable before launching nwn. Edit the nwn script and add the following line before the "./nwmain $@" command :


This actually worked for me!  It was honestly the first thing I tried, since I was very hesitant to disable kernel mode, and right off the bat it made everything run perfectly smooth.

Thanks all!  I'm off to play some Neverwinter Nights now!

---

### Post by Skildron on 2012-06-20
Good to know that you can play NWN now. Though I am confused now: GL_NV_vertex_program is a nvidia OpenGL extension. Since neither of you has an nvidia graphic, this extension should not be there in the OpenGL libs at all and so there should not be any need to disable it.

I will reserch this a little bit more.

Greetings 
Skildron

---

### Post by scorpiosnake on 2012-07-07
> **Sanus Compleo said:**
> This actually worked for me!  It was honestly the first thing I tried, since I was very hesitant to disable kernel mode, and right off the bat it made everything run perfectly smooth.

Thanks all!  I'm off to play some Neverwinter Nights now!

I was having the same problem and this solution fixed it for me as well. So for anyone else having this problem, before doing anything else try this simple fix first.

---

### Post by dorohoro on 2013-02-23
After did this i had no problem with texture but game become to slow to play. Before it work extra fast and no lag

---

### Post by gtmaneki on 2013-03-04
> **jemino said:**
> I had the same problem with the invisible bodies when robes or cloaks where equipped (using a Sandy Bridge GPU). I seem to have solved it by disabling the GL_NV_vertex_program OpenGL extension.

The best way to do this should be to set the MESA_EXTENSION_OVERRIDE environment variable before launching nwn. Edit the nwn script and add the following line before the "./nwmain $@" command :

```

...
export MESA_EXTENSION_OVERRIDE=-GL_NV_vertex_program
./nwmain $@

```

This worked for me, even though I was playing through PlayOnLinux.  I just ran the export command before I started PlayOnLinux.  Thanks for figuring this out!

---

### Post by robert63 on 2014-02-23
> **gtmaneki said:**
> This worked for me, even though I was playing through PlayOnLinux.  I just ran the export command before I started PlayOnLinux.  Thanks for figuring this out!

I know it's a bit later... but do you remember if there was anything special to do this? I'm exactly in this situation (Intel Sandybridge as well). I've tried running the export command in a terminal and then opening playonlinux to run NWN, but the glitchy robes are still there. Was there anything else to it?

Thanks in advance for any help!

---

