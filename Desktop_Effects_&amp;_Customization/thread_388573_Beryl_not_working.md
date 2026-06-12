---
title: "Beryl not working"
date: 2007-03-19
forum: Desktop Effects &amp; Customization
---

### Post by Chaos_Slug_164cm on 2007-03-19
OK I tryed to get beryl working on my computer but it wont run for somereason. its installed and I can see it in the system tray but the splash screen dosn't pop up when I run it and the visuals don't run ether.

Any idea on how to get it to work?

---

### Post by Waappu on 2007-03-19
Hi

What guide you followed to install beryl?
Type in terminal```
lspci
```and post output of that so we know what video card you have.
Type also in terminal```
beryl
```and post error messages

---

### Post by Chaos_Slug_164cm on 2007-03-19
as for my video card I have a radeon 9600 with 128mb ddr Don't know if that helps.

---

### Post by Chaos_Slug_164cm on 2007-03-19
```

00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)
02:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
02:0a.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 08)
02:0c.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)

```


and when i input beryl i get this 
```
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

```

---

### Post by Waappu on 2007-03-20
Hi

Type in terminal```
gksudo gedit /etc/X11/xorg.conf
```and add these lines to end of file or check that composite isn't disabled```
Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

---

### Post by Chaos_Slug_164cm on 2007-03-20
Ok I Enabled composite.

Not sure if its suppose to work now but it's still not running all the 3D interface stuff

Oh yea as for installe guid i'm pretty sure I used this one
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)
I'm just not 100% sure. I got really bad memory sometimes.

---

### Post by Waappu on 2007-03-20
Hi

Ok, so you try to run XGL according guide you post.

Did you install fglrx drivers ??
Use envy to install that driver
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

When you use that driver composite needs to be disabled and you need to login to XGL session.

---

### Post by Chaos_Slug_164cm on 2007-03-20
I'm pretty sure i got that installed.

Is there a terminal command to double check?

---

### Post by Waappu on 2007-03-21
Hi

I don't know is there terminal command but if you open Synaptic and find xserver-xgl and is that installed.
And if you can find file /usr/local/bin/startxgl.sh in your system and it's content match to guide.
Then you have installed XGL and you should login to XGL session.

---

### Post by Chaos_Slug_164cm on 2007-03-22
Got beryl to work. 

The only problem I have with it is that its slow. I don't know why its running slow.

my system specs

1.8ghz p4 
640mb ram
9600 128mb ddr
and a 20gb hard drive.

It should be running buttery smooth because hell Vista buisness with aero runs decently smooth.

what gives?

---

### Post by jtchupp on 2007-03-22
Uninstall your ati drivers and use [envy]("http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu3_all.deb") to reinstall them.

---

### Post by Chaos_Slug_164cm on 2007-03-22
Thanks!

---

