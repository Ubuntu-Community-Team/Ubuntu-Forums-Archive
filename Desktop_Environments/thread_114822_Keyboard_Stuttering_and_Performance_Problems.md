---
title: "Keyboard Stuttering and Performance Problems"
date: 2006-01-09
forum: Desktop Environments
---

### Post by glynor on 2006-01-09
First of all, I wanted to say hello all!  I'm a new Kubuntu user (switched from Fedora a few weeks ago).  While I am by no means an expert Linux user, I am a very experienced OSX and Windows user.  Okay, that said...

I'm having trouble with my new Kubuntu (5.10) installation.  Right out of the gate I'm having severe, though inconsistent, performance problems.  I am periodically having trouble with input.  The mouse pointer will begin "skipping" around (often causing me to click on the wrong thing), and my keyboard input becomes extremely erratic (often skipping letters I typed or suddenly repeating one character until I press another key on the keyboard).  While this is happening, I typically notice fairly heavy disk usage (though I am not at all sure that these things are related).  I did check the CPU load and memory usage while it was happening last night, though, and nothing seemed unusual (2-3% overall CPU usage and over half of my Physical Memory free).

As I mentioned, though, this is not consistent.  Much of the time, the system performs perfectly and smoothly.  It seems to go through "storms" of problems, which occur seemingly at any time:  sometimes after I've been using the system for a while, sometimes right at boot-up before I even log-in (and the keyboard problems make logging in very difficult), and sometimes after the system has been sitting idle for a while.  The "storms" also seem to pass on their own...

Some details about the system:
[LIST]
[*]Completely fresh Kubuntu 5.10 install (installed from DVD iso). (The only things I did was run the system updates through Adept and install FireFox 1.5 in /opt/ but the problem exhibited prior to these changes as well).
[*]Asus A7N8X-X Motherboard
[*]Athlon XP 2000+ CPU (clocked at stock)
[*]1 GB Crucial PC3200 RAM
[*]60 GB WD ATA100 Hard drive
[*]IOGear MiniView Micro USB PLUS KVM Switch [GCS632U]  (with plain vanilla Microsoft USB mouse and G4 Mac keyboard attached).  The other machine attached to the KVM is a Mac G4.
[*]The system's hardware was tested fairly extensively before installing Kubuntu: 24 hours+ Memtest86 with no errors, and 12 hours+ of Prime95 (both run via Ultimate Boot CD 3.3)

[/LIST]

I, of course, suspect my KVM switch as the culprit.  However, the connected Mac exhibits NONE of these problems.  I also last night installed the ubuntu-desktop package and tried out Gnome.  I didn't use it for an extremely long time, but the problem never manifested while using the Gnome desktop.  I haven't yet tried to use the system without the KVM (using the mouse and keyboard direct) but I intend to give that a go within the next day or two.  Also, the exact same KVM setup didn't have any problems with Fedora (it was the same Keyboard, mouse, and KVM switch though the Fedora install was on a different machine... the current Kubuntu box is my old primary Windows machine though, which was used heavily, and never had any major problems).

Assuming that it is either a problem with a) the USB KVM, or b) the Mac USB keyboard ... Is there anything that can be done other than abandon my Mac/Linux KVM setup?  I really like Kubuntu so far (when it works), but it isn't usable currently.  I also wonder if this is something Dapper might address (and if so, is it stable enough for me to try on a non-essential machine)?

---

### Post by Thirsteh on 2006-01-09
Hello.

Please do this:
sudo hdparm -i /dev/hda

And tell me what mode your drive is currently set to.

Should look something like this:
> /dev/hda:

 Model=IC35L120AVVA07-0, FwRev=VA6OA50K, SerialNo=VNC600A6G1HE3A
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=52
 BuffType=DualPortCache, BuffSize=1863kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=241254720
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-5 T13 1321D revision 1:

Where "*" at udma5 indicates I'm using that mode.

I have a slight suspicion that it may be due to your harddrive running in PIO mode as that happened to me before and all input was slowed down for some reason.

---

### Post by glynor on 2006-01-09
Thanks.  That would make sense.  I can get that output this evening (I'm at work right now).

---

### Post by Thirsteh on 2006-01-09
Alright, I'll try to remember the thread and check back on it. I must admit I'm a bit of a "forum runner" or ...troll. ;)

---

### Post by glynor on 2006-01-09
Well... It looks like it isn't that.  I did discover that I was wrong about which Hard Drive I had installed in this machine, but it is in UDMA mode (though this older Seagate drive only supports UDMA4 (rather than 5).  That shouldn't make much of a difference though...

```
/dev/hda:

 Model=ST330630A, FwRev=3.21, SerialNo=3CK07MTH
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=59777640
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 *udma4
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: device does not report version:  1 2 3 4
```

Typing this message on the Kubuntu machine has been quite irritating.  Any other ideas?

---

### Post by glynor on 2006-01-09
Well... It looks to be definitely a KVM related problem.  I'm typing this on my Kubuntu box with the exact same mouse and keyboard plugged in directly, and it's working just fine.

Apparently I'm not the only one having problems with a KVM and Ubuntu (once I searched for KVM in the forums I came up with a bunch of hits).  Most of the people seem to be complaining about the mouse though.  My mouse is not perfectly responsive, but it seems to be "mostly" working (compared to what the other people are indicating).

Luckily, I have access to another KVM.  It will break some of the functionality on my Mac (the eject and other function keys won't work anymore) but I'm going to give it a go and see how it works.

---

