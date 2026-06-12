---
title: "Second monitor not working after installing new card"
date: 2011-03-05
forum: Desktop Environments
---

### Post by atomicben on 2011-03-05
I just installed a second video card hoping to get dual monitors (dual desktops) going.  Although lspci shows both cards but SYSTEM > PREFERENCES > MONITORS only shows the primary.

Here's the setup:

OS:
Maverick 10.10
2.6.35-27-generic-pae

Motherboard:
ASROCK G31M-S

Video Card 1 (ONBOARD) primary:
Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)

Video Card 2 (PCI) secondary:
VGA compatible controller: ATI Technologies Inc 3D Rage Pro (rev 5c)

BIOS is set to use OnBoard (Intel G31) as primary because:

While BIOS set to OnBoard** both cards are shown in lspci** but only primary monitor (on the intel G31) works.

While BIOS is set to PCI the secondary monitor (on ATI Rage Pro) comes to life **BUT only the ATI shows in lspci**.  Therefore, I've got it set to OnBoard to make sure I have both showing.


lspci | grep VGA
```

00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
03:01.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro (rev 5c)

```dmesg | grep vga
```

[    0.257590] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.257632] vgaarb: device added: PCI:0000:03:01.0,decodes=io+mem,owns=none,locks=none
[    0.257639] vgaarb: loaded
[   13.166358] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   13.166368] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:03:01.0

```There is also a screenshot attached showing the Monitor Preferences screen.

Can you help?

BTW I've tried removing, installing and reconfiguring xorg:
```


sudo apt-get remove --purge xserver-xorg
sudo apt-get install xserver-xorg
sudo dpkg-reconfigure xserver-xorg

```

---

### Post by atomicben on 2011-03-05
Update:  
I tried installing the fglrx with Catalyst Control Center but it made no difference.  It didn't see the card.  I suspect it's really only for Raedon cards not this Legacy All In Wonder Pro that I have.  

What's driving me nuts is that if I switch the BIOS to use PCI as primary video the card/monitor works so obviously it's supported.  Because of that I really don't know where the problem lies....


[LIST]
[*]It could be my MoBo/Chipset but I can't find any documented limitations that would prevent dual monitors.
[/LIST]


[LIST]
[*]It could be in the BIOS (meaning X doesn't have any control) but I don't see anything that would enable/disable a secondary card/monitor.  It doesn't have an AUTO choice that's causing this, it's PCI, PCI Express or OnBoard.
[/LIST]


[LIST]
[*]I am thinking it's an OS thing because the card shows in lspci and dmesg doesn't show any problems.  But again, it can't be the driver because when I switch the BIOS to PCI it works fine so it's not as if Ubuntu doesn't support this card.
[/LIST]

I'm racking my brain but nothing is coming out.  Any help/advice would be appreciated.

---

### Post by atomicben on 2011-03-05
Another Update:

lshw -C display
```

*-display               
       description: Display controller
       product: 82G33/G31 Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:fe980000-fe9fffff ioport:cc00(size=8) memory:d0000000-dfffffff memory:fe800000-fe8fffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: 3D Rage Pro
       vendor: ATI Technologies Inc
       physical id: 1
       bus info: pci@0000:03:01.0
       version: 5c
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller
       configuration: latency=32 mingnt=8
       resources: memory:fd000000-fdffffff ioport:e000(size=256) memory:febef000-febeffff memory:febc0000-febdffff

```

What does unclaimed mean?  How do I claim it?  I'm lost.  :(

---

### Post by robsoles on 2011-03-05
Please post the contents of your /etc/X11/xorg.conf file.

---

### Post by atomicben on 2011-03-05
> **robsoles said:**
> Please post the contents of your /etc/X11/xorg.conf file.

It doesn't exist.  Apparently in Maverick it's not required any more.
$ /etc/X11$ ls

```
app-defaults             fonts    xinit   Xreset.d    Xsession.d
cursors                  rgb.txt  xkb     Xresources  Xsession.options
default-display-manager  X        Xreset  Xsession    Xwrapper.config

```

---

### Post by robsoles on 2011-03-05
No longer required doesn't mean not usable anymore.

Have a look at these, particularly in last couple of posts in the second one.
[http://ubuntuforums.org/showthread.php?t=121691](http://ubuntuforums.org/showthread.php?t=121691)
[https://bbs.archlinux.org/viewtopic.php?id=106243](https://bbs.archlinux.org/viewtopic.php?id=106243)

---

### Post by atomicben on 2011-03-06
> **robsoles said:**
> No longer required doesn't mean not usable anymore.

Have a look at these, particularly in last couple of posts in the second one.
[http://ubuntuforums.org/showthread.php?t=121691](http://ubuntuforums.org/showthread.php?t=121691)
[https://bbs.archlinux.org/viewtopic.php?id=106243](https://bbs.archlinux.org/viewtopic.php?id=106243)

Sincerely - Thanks for your time.

I have learned that you can still create an xorg.conf and that after doing so it will be the boss, that's what scared me.  I've checked other forums while investigating this problem and I've seen some folks completely f-up their system after making an xorg.conf.

I am not prepared to take a risk like creating my own from scratch.  I've seen some other forums mention that if i do something like xorg --config it will create a basic xorg.conf... I've tried what they suggested and I still don't have an xorg.conf file so the fear is gripping me.  If something weird/bad happened I'd kernel panic in my gitch.

Anyway, I'll check your suggestions tomorrow as I'm too tired (drunk) to make sense of them.  I'll update my progress as I go.

Thanks again,

Ben

---

### Post by robsoles on 2011-03-06
Unless I am sorely mistaken you don't need to make an /etc/X11/xorg.conf file to use a file at /etc/X11/xorg.conf.d/20-ati-3d-rage-pro.conf with contents something along the lines of
```
Section "Device"
    Identifier  "[COLOR=Red]ATI-00001[/COLOR]"
    Driver      "[COLOR=Red]fglrx[/COLOR]"
    VendorName  "ATI"
    BoardName   "3D Rage Pro"
    BusID       "[COLOR=Red]PCI:0:3:1[/COLOR]"
EndSection
```I've marked the things in red there that need double checking before you go booting up with this file in it's intended place - you can just delete this file using the terminal from a GUI-borked boot or a LiveCD if it makes trouble for you on restarting.

A fairly straightforward way create the file and give it that content is to pop the following in terminal and then copy and paste from above, quit gedit and choose the option to save changes.```
sudo md /etc/X11/xorg.conf.d
gksudo gedit /etc/X11/xorg.conf.d/20-ati-3d-rage-pro.conf
```

Any good? :)

---

### Post by atomicben on 2011-03-06
ubuntu wouldn't boot - not even my maverick live usb.  I think the live usb also checks these locations when booting.  I had to pull out an old gparted live cd and learn to mount a drive in the terminal to finally delete our new file.  

Now, that being said I didn't follow your instructions exactly  :)

the reading I've done has told me that the xorg.conf.d is located @ /usr/share/X11/xorg.conf.d for Maverick so that's where I put our new file.  I hope that wasn't the cause of the problem.

I tried editing the contents as you suggested.  Here's what I put together:

```

Section "Device"
    Identifier  "ATI-00001"
    Driver      "fglrx"
    VendorName  "ATI Technologies Inc"
    BoardName   "3D Rage Pro"
    BusID       "PCI:03:01.0"
EndSection

```I left the Identifier alone because I couldn't find any info that looked like that in my lshw or lspci.  Maybe that's wrong.

I left the driver as fglrx but that is not on my system.  I had tried installing that earlier but removed it after it didn't seem to do anything.  Should I reinstall it and try again?

I changed VendorName, BoardName and BusID to match the info I found in my lshw and lspci.  I wasn't sure about the BusID because it looks different than your example but that's exactly how it looks in lspci.  in lshw it looks different too: 
bus info: pci@0000:03:01.0 so I really don't know what to put.

I've also noticed in lshw that my Intel card has an IRQ assigned while this ATI doesn't.  Is that simply because it's still unclaimed or could there be an IRQ conflict?

So I'm kinda back at square 1 again.  I don't want to keep tweaking this file, rebooting and having to rescue my system, it's terrifying.

From what I've told you, do you have any suggestions?

Thanks your patience.

---

### Post by robsoles on 2011-03-06
There may be a BIOS setting as to whether or not PCI cards get assigned IRQ and it could be a matter of it being unclaimed - have a quick poke through BIOS but let's not get hung up on it at this point.

If fglrx is the right driver for the ATI 3D Rage Pro (haven't used one under Linux to be honest) then it needs to be installed otherwise the right driver needs installing and naming at that point of this file.

I think the PCI ID is right.


It is probable that it failed due to the driver being named but not actually present on your system but I've been wrong before.

---

### Post by atomicben on 2011-03-06
Hay man, thanks for all your help.  I'm giving up.  I've tried:

Section "Device"
    Identifier  "ATI All-in-Wonder/Rage Pro"
    Driver      "vesa"
    VendorName  "ATI Technologies Inc"
    BoardName   "3D Rage Pro"
    BusID       "PCI:03:01.0"
EndSection

and

Section "Device"
    Identifier  "ATI All-in-Wonder/Rage Pro"
    Driver      "mach64"
    VendorName  "ATI Technologies Inc"
    BoardName   "3D Rage Pro"
    BusID       "PCI:03:01.0"
EndSection

and both times I get locked out of X.  I've heard of a bunch of things that can cause problems with this device and worst of all people say that once it's installed it's slow anyway.

BTW, I think that fglrx is for raedon chipsets only.

I'm just going to find another old cheapie card and give it a shot.  I may even have an old nVidia laying around, I just gotta look for it.

Catch ya later.

---

