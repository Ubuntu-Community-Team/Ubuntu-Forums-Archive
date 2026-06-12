---
title: "Suspend on Dell Inspiron 6000"
date: 2006-05-24
forum: Desktop Environments
---

### Post by ScatterBrain on 2006-05-24
I've been trying out Dapper for the past several weeks on my Inspiron 6000.  The main reason for this is to get two thing working that Breezy could never do on it:[LIST]
[*]Suspend to Ram
[*]SD Card Reader[/LIST]Thanks to the latest round of Dapper updates, I've been able to get the SD Card Reader working fine.  GREAT WORK GUYS!!!

But, suspend has never worked - well at least never 100%.  I've always been able to suspend the machine.  I've just never been able to make resume afterwards.  What really ticks me off is that SEVERAL people on blogs, forums and mailing lists say that it works on their Inspiron 6000 out of the box!  And this is even with Breezy.  So I'm wondering what I'm doing wrong.

The machine suspends/resumes just fine in Winblows, so I know it's not the hardware.  I'm not using the accelerated ATI Drivers - although I would like to.  I did a fresh install of Dapper Beta 2 yesterday fully updated the setup.  I've not installed anything yet - just the standard desktop.

The machine suspends - I wake it up and the power light comes on, the bluetooth LED comes on, the Hard drive it hit for a split second and then nothing.  I can't switch to another terminal, I can't SSH into the machine, I can't get the LCD to light up - it's just dead.

So, anyone willing to help me figure this out?

If it matters, my machine has the following hardware:[LIST]
[*]Pentium-M (Centrino) 2.0 GHz
[*]2GB RAM
[*]60GB Hard Drive
[*]8x DVD/RW Drive
[*]128MB ATI Radeon X300
[*]Intel Pro/Wireless 2200 (BG)
[*]Broadcom 4401 Wired NIC
[*]Intel WinModem
[*]Intel AC97 Sound Card
[*]Intel 915GM Chipset (I think)
[*]Ricoh SD Card Reader
[*]Ricoh Firewire Controller
[*]Dell Internal Bluetooth Adapter (the Wireless 350 I think)[/LIST]

---

### Post by rob.webinator@gmail.com on 2006-05-24
Any luck with this?
I have dapper Beta2 and suspend does not work for me. Computer: Dell 9100 with ATI 9700. When I select suspend, it appears to go into suspend but when I try to resume, I get this strange dark screen with a diffusing blob on it that moves around and the screen looks tiled. It's weird. Any thoughts?

---

### Post by snyperx on 2006-05-24
I may have to keep looking at this thread because I have a Inspiron 600m that has the same issue.  I can suspend fine, but am unable to resume successfully.  I just get a black screen.  Only way to bring it back up s to power off and back on again.

---

### Post by rado_london on 2006-05-24
Same with HP Pavilion dv4000. SO it isnt Dell issue it is general issue. DEVS wake up!

---

### Post by ScatterBrain on 2006-05-24
Well, because I have nothing better to do today, and I've not got to worry about backing up, I'm going to try Fedora Core 5 this afternoon.  Suposedly, with FC5 on the Inspiron 6000, everything works - including suspend and the SD Card.  Every article that I've turned up with Google says so.  But, there's really only one way to find out.

I'll report back with any findings.

---

### Post by cleentrax on 2006-05-24
I have the same problem with the default settings in Dapper. But the Ubuntu Wiki has a solution, at least for me, and for others with Nvidia drivers:

[https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend](https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend)

---

### Post by Jawbreaker4Fs on 2006-05-24
Does anyone know if there's a way to get the SD card reader working in Breezy without having to recompile the kernel? I've seen several guides about this but they all require doing some kernel modifications that I'm not exactly sure about. I'm getting a gp2x later this week, and I wanted to use the SD reader for that. If not I guess I'll just wait another week for the Dapper release, I hear it works with that out of the box.

---

### Post by SonWon on 2006-05-24
I have the same problem with ATI video.

---

### Post by gregh on 2006-05-24
At the risk of a "me to" type of situation, I also have this issue.
My laptop is a brand new HP pavillion dv5000, (intel dual core)

Suspend, but no wake up. Sometimes it almost wakes up but then reboots itself.

I have tried every howto I can find but no joy.

If anyone has ideas I am willing to act as a test bed to get these issues ironed out.

-Greg

---

### Post by Egalus on 2006-05-25
Maybe searching this forum might have helped to understand why the i6000 has problems resuming and also to find a way around it:
[http://www.ubuntuforums.org/showthread.php?t=141362](http://www.ubuntuforums.org/showthread.php?t=141362)

(especially my posts in there might help if you want to put a little bit of work into it).

---

### Post by _flyman_ on 2006-05-30
[QUOTE=ScatterBrain]I've been trying out Dapper for the past several weeks on my Inspiron 6000.  The main reason for this is to get two thing working that Breezy could never do on it:

[LIST]
[*]Suspend to Ram
[*]SD Card Reader
[/LIST]

Thanks to the latest round of Dapper updates, I've been able to get the SD Card Reader working fine.  GREAT WORK GUYS!!!

But, suspend has never worked - well at least never 100%.  I've always been able to suspend the machine.  I've just never been able to make resume afterwards.  What really ticks me off is that SEVERAL people on blogs, forums and mailing lists say that it works on their Inspiron 6000 out of the box!  And this is even with Breezy.  So I'm wondering what I'm doing wrong.

The machine suspends/resumes just fine in Winblows, so I know it's not the hardware.  I'm not using the accelerated ATI Drivers - although I would like to.  I did a fresh install of Dapper Beta 2 yesterday fully updated the setup.  I've not installed anything yet - just the standard desktop.

The machine suspends - I wake it up and the power light comes on, the bluetooth LED comes on, the Hard drive it hit for a split second and then nothing.  I can't switch to another terminal, I can't SSH into the machine, I can't get the LCD to light up - it's just dead.

So, anyone willing to help me figure this out?

If it matters, my machine has the following hardware:

[LIST]
[*]Pentium-M (Centrino) 2.0 GHz
[*]2GB RAM
[*]60GB Hard Drive
[*]8x DVD/RW Drive
[*]128MB ATI Radeon X300
[*]Intel Pro/Wireless 2200 (BG)
[*]Broadcom 4401 Wired NIC
[*]Intel WinModem
[*]Intel AC97 Sound Card
[*]Intel 915GM Chipset (I think)
[*]Ricoh SD Card Reader
[*]Ricoh Firewire Controller
[*]Dell Internal Bluetooth Adapter (the Wireless 350 I think)
[/LIST][/QUOTE]
try going to > etc/default/acpi-support
1.uncomment the line > acpi_sleep=true
2.make sure this line is as follows> ACPI_SLEEP_MODE=mem

also change this file > value/etc/acpi/events/lidbtn
to

event=button[ /]lid
action=/usr/sbin/pmi action sleep

---

### Post by gregh on 2006-05-30
Well, I am almost there. The issue now is:
Closing lid will sleep (yay!)
Opening lid will resume (yay!)

but after about 1 second ( the mouse in inactive as well ), the laptop shuts itself down boo :-(

so almost, but no cigar.

any more help?
I am happy to try any suggestions

-Greg

---

### Post by nealklomp on 2006-05-30
its funny this thread, cause I have Insperion 6000, with built in wifi, 1.6 celeron, out of the box no problems with sleep, etc. going to switch up to dapper, then take a week off to make my box perfectly tweaked, with everything exactly as I want it.
But first to try dapper on a partition.

---

### Post by drFUNK on 2006-06-15
If anyone is still following this issue, it seems that the newest kernel update (2.6.15-25-386) fixed this issue on mine.  Did it help anyone else out?

---

### Post by wundbread on 2006-06-17
YES!!! I just resumed from a suspend even running fglrx...  wow, now EVERYTHING works.  Good job ubuntu!

---

