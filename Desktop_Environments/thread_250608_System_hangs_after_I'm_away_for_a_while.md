---
title: "System hangs after I'm away for a while"
date: 2006-09-04
forum: Desktop Environments
---

### Post by ssmokn on 2006-09-04
I'm hoping to get some tips on how to peform proper problem determination on this problem (what logs/settings to check etc.)

I'm relatively new to Linux and Ubuntu.  I have been using Ubuntu for about a month or so.  I like it so much I've switched entirely from Windows XP.  I decided to build a new "low cost" machine to use as my "experiemental" Ubuntu box for learning purposes (so I have my main PC running Ubuntu and another one running for Ubuntu that I can mess up when necessary :D ).

This new box was put together from relatively inexpensive parts.  I purchased an AMD 64 3400+ 2.4GHz processor from one of the online vendors and it came with bundled with a Gigabyte GA-K8VM800M (rev 2.0) motherboard (VIA based) for free.  I never was a huge fan of Gigabyte motherboards but it had some positive reviews and since I was trying to keep the price down I figured what the heck.  I have also upgraded the BIOS to the latest revision 12/2005.  I'm running PS/2 style mouse and keyboard (IBM keyboard with built in trackpoint).  Monitor is an IBM ThinkVision L190p.

I'm using internal video, ethernet and sounds on this board along with a SATA Western Digital 250GB drive, 2GB of Corsair DDR400 memory and an LG DVD R/W.

Ubuntu installed fine, recognized everything and is generally working great.  I have 6.06.1 with all the patches.

The only problem I'm having is that after I'm away for a while (say 30 minutes or more) when I return to the screen saver (or a blank screen) the machine is non-responsive to keyboard input.  I cannot get back to the Desktop login by pressing any combinatio of keys.

I have to hit the hard reset button on the box to reboot and them I'm fine until the next time.  Power settings are all defaults.

What is the best way to debug?  Any logs or settings I can check.  Aside from this everything is working great.

Here is output of lspci.  If any other info. is needed let me know.  Thanks!

0000:00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)

Also running the current K7 kernal --> 2.6.15-26-k7

---

### Post by peabody on 2006-09-04
Turn off the screensaver and see if it fixes your problem.  If it does, it's likely the video doesn't like opengl.  Looking into video drivers is the likely fix.

If that doesn't seem to be it, you're going to want to look at the output of /var/log/dmesg upon reboot.

---

### Post by iONiK on 2006-09-04
> **peabody said:**
> Turn off the screensaver and see if it fixes your problem.  If it does, it's likely the video doesn't like opengl.  Looking into video drivers is the likely fix.

I quote.

---

### Post by jimbob on 2006-09-04
If the screensaver isn't the culprit, it may be acpi.

Try booting with the kernel options noacpi and acpi=off.

Also check the acpi settings in your bios.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by ssmokn on 2006-09-04
Thanks for the suggestions.  I will try them one at a time and report back the net results.

---

### Post by ssmokn on 2006-09-05
I think that peabody hit the nail on the head.  I disabled screensaver and machine has been fine since.  I think it is OpenGL.

This board does have the S3 Unichrome video.  I have to search around more.  I found some info but I need to dig deeper to get a better understanding of what options I have.  

Anybody using this board that has looked into the S3 unichrome drivers?  If so I'd love to hear what you did.   Thanks again for all the assistance!

---

### Post by jimbob on 2006-09-05
I also have a system with the VIA S3 Unichrome display.

Check out these two links:

[http://www.ubuntuforums.org/showthread.php?t=184512&highlight=K8M800](http://www.ubuntuforums.org/showthread.php?t=184512&highlight=K8M800)
[http://www.ubuntuforums.org/showthread.php?t=76037&page=3&highlight=K8M800](http://www.ubuntuforums.org/showthread.php?t=76037&page=3&highlight=K8M800)

Everything is working OK on mine as far as it goes but no 3D stuff is available yet.

If you wade through all the forums the general consensus is that we will have to wait for newer drivers to be released.

Make sure you have xserver-xorg-via installed.  Ubuntu has the latest available I believe.

I had to go through and delete four of the screensavers because they completely locked up my (actually my lady friend's) system by just selecting them:  Flipscreen3D, AntSpotlight, Lattice and Matrixview.

She no longer sees these as selections.

---

