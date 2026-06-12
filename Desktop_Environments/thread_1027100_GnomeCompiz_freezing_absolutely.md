---
title: "Gnome/Compiz freezing absolutely"
date: 2008-12-31
forum: Desktop Environments
---

### Post by jamesisin on 2008-12-31
I'm not sure this is the best area for this thread, but since the problem is as yet a little unclear I'll start here.

For some reason, my system (8.10) has been freezing from time to time--and lately at an increasing frequency.  It is making the machine rather impossible to use.

Nothing is leaping out in the logs, but I could certainly be overlooking something important.

When it freezes, it fully kicks over.  The mouse loses its laser light, the keyboard won't do anything (no ctl-alt-del, ctl-alt-backspace, no caps-lock), and I get time out errors on ssh requests (normally they would be refused).

I'm happy to provide any information I am able.  Just point me in the right direction.

I have tried not running the following apps to rule them out: Trillian (under Wine--only Wine app); Compiz (changed Desktop Effects to None); Thunderbird; Skype.  It will still freeze with any of those closed.

---

### Post by keithld on 2008-12-31
James could you post the "Specs" of your computer???... Have you a way to check the Temps of your CPU???...

Have you checked to see if all your Fans are running as they should be???...

It almost sounds like an "Temporary Overheating Problem" but I'm not sure... Once you post your Specs I'm sure some of the experts here will better be able to help you... :D

---

### Post by jamesisin on 2008-12-31
The machine itself is a Dell Dimension 8300 with 4gb of RAM (3.6 acknowledged).

Any other hardware I can report on?  I may need to use a specific command because I don't really have any paperwork on the box or its cards.

Also, is there a systemic way to find out the CPU temperature?

Both fans appear to be spinning normally enough.

---

### Post by keithld on 2008-12-31
Is it still under Warranty with DELL? & did it come Installed with Linux or did you do that your self???...

The reason I ask is maybe you could call them and see what they say...

Other than that I think when some of the others get online they will have some ideas for you, outside of that it's possible since your losing the mouse power and the keyboard that it could be a Motherboard problem or maybe a Power Supply problem...

I'd wait and see what others have to say...

---

### Post by jamesisin on 2009-01-01
Yeah, I'm guessing it's software and not hardware.

This machine is an antique, as far as that goes.  Not so long ago I built it with 8.10.  Before that it was running XP without any issues (for a long time).  It's been running pretty much fine until just recently when this issue rather crept up.

There are a number of things I haven't yet ruled out, software-wise: Opera, Transmission, Gnome itself, and many services.

I just installed the ssh client so I can run top (or some other command?) from my laptop while I try to crash this box.

---

### Post by keithld on 2009-01-01
I'm a Linux n00b so I was throwing some ideas at you to see if any would help...

Like I said the Experts here should have a better idea about what's going on... Hang in there...

---

### Post by jamesisin on 2009-01-01
This may have fixed it:

[http://ubuntuforums.org/showthread.php?t=976610](http://ubuntuforums.org/showthread.php?t=976610)

I'll report back if that's not the case.  I'll change the title tomorrow.

---

### Post by Rohan Kapoor on 2009-01-01
> **jamesisin said:**
> This may have fixed it:

[http://ubuntuforums.org/showthread.php?t=976610](http://ubuntuforums.org/showthread.php?t=976610)

I'll report back if that's not the case.  I'll change the title tomorrow.
I don't think that the home/user/.dmrc file should effect your system freezing. More likely it is overheating. Could you give us the output of the command:
```
lspci
```

---

### Post by jamesisin on 2009-01-01
Sure.  Though I have to say, since I changed that my freezing has stopped.

```
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
```

And it wasn't just the .dmrc file.  It was my home directory: it was set, somehow, to allow all users edit rights.

---

### Post by Rohan Kapoor on 2009-01-01
> **jamesisin said:**
> Sure.  Though I have to say, since I changed that my freezing has stopped.

```
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
```

And it wasn't just the .dmrc file.  It was my home directory: it was set, somehow, to allow all users edit rights.
Alrighty then! Glad to see it's Fixed!

---

### Post by zee on 2009-01-09
I have a similar problem. Since I do a lot fo hardware testing I sometimes plug my keyobard to another computer. When I plug it back into my desktop  X11 (i.e. Gnome) freezes and I have to do a hard reset.

No errors are found in the log files.

I'm using Ubuntu 8.10 (amd64).

Thanks in advance,
zee

---

### Post by jamesisin on 2009-01-11
Well, I hope you are using a USB keyboard, because if you are hot-swapping a PS2 keyboard that will often freeze a system.

My freezing issue came (somehow) from my home and .dmrc permissions being incorrect.  I have corrected that and my freezing has disappeared.

---

### Post by zee on 2009-01-12
I use a USB keyboard and mouse, so this is not the reason for the observed freezing.

zee

---

### Post by Rohan Kapoor on 2009-01-12
> **zee said:**
> I use a USB keyboard and mouse, so this is not the reason for the observed freezing.

zee
Have you checked your permissions on your /home/user/.dmrc file?

---

### Post by jamesisin on 2009-01-12
If your .dmrc file is not set (permissions) correctly, you ought be getting a warning at login.  Is that the case?

Does swapping any other USB device (mouse, drive, camera, &c) cause the freezing?

Can you try a different keyboard to see using a different (USB) keyboard also freezes your system?

---

