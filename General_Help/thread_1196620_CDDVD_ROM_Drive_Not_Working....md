---
title: "CD/DVD ROM Drive Not Working..."
date: 2009-06-25
forum: General Help
---

### Post by Noobs*McGee on 2009-06-25
Okay, I'm very new to Ubuntu so bear with me here:

I've searched Google and the forums up and down for some help with this, but nothing I've found was much help - most of the results I came up with either didn't address the problem I'm having or were  too complicated for me to understand

The problem I'm having is that my CD/DVD Drive no longer seems to be recognized by Ubuntu.  I'm actually not entirely sure when this started, because I only very recently noticed it when I went to play a DVD movie.  After reading the help documentation, I thought the problem might be that I didn't have one of the packages needed to play DVDs or something, but even after making sure all the listed packages (libdvdnav4, libdvdread4, gstreamer0.10-plugins-bad and gstreamer0.10-plugins-ugly, and libdvdcss2) were installed, the problem persisted.

Then when I went to burn a DVD using Brasero, I encountered a further problem when the program didn't seem to recognize that the there was a blank DVD in the drive.

I'm completely lost here, not even sure where to start :confused:  I'm not sure how to tell if Ubuntu is recognizing my CD/DVD drive or not, or what the directory is to the drive if it is...  It seems like the drive was working fine when I first installed Ubuntu, because I remember putting the Live CD in again after I'd installed just to check that it read it.  I hadn't really tried to use the drive for anything for a while, since most of my music and video is stored on an external HDD, so I'm really not sure when this problem arose, or even if it has been an issue since install (though I don't think it has... I imagine something got messed up along the way...)

My system specs (what I know of them) are as follows:
I'm running Ubuntu 9.04 Jaunty Jackalope on a Toshiba M45 Series Satellite Laptop with factory CD/DVD drive (not sure the specifics of the drive)

Any help would be immensely appreciated.  I feel like I'm probably gonna need drive functionality at some point ;)

---

### Post by Noobs*McGee on 2009-06-25
oh, one more thing: I just remembered I changed the boot device order in the BIOS a short while ago, I'm not sure if that would have anything to do with this? (I doubt it, but I'll try changing it back and see what happens...)

---

### Post by khelben1979 on 2009-06-25
Open up a text shell like [xterm]("http://en.wikipedia.org/wiki/Xterm") for instance and type this:
```
df -h
```

Then copy and paste it's output in this thread. It will show if your cd/dvd rom drive has been identified and if it's been mounted by the system.

---

### Post by Noobs*McGee on 2009-06-25
This is the output I get when I type df -h in Terminal:

Filesystem  Size   Used  Avail  Use% Mounted on
/dev/sda1                 89G      32G      52G   39%  /
tmpfs        498M     0     498M      0%  /lib/init/rw
varrun      498M    116K   498M      1%  /var/run
varlock                   498M          0     498M    0%  /var/lock
udev                          498M  152K  498M    1%  /dev
tmpfs                        498M      88K   498M      1%  /dev/shm
lrm                             498M   2.2M  496M      1%  /lib/modules/2.6.28-13-generic/volatile

I don't see anything that looks like a cd drive, but then I have no idea what most of that means (the only thing I recognize is the main HD partition...)

---

### Post by khelben1979 on 2009-06-25
From the output I can see that the cd/dvd rom isn't mounted, however it does not mean that it isn't identified by the Linux kernel.

Have you been able to see during startup if the cd/dvd rom drive has been identified?

---

### Post by Noobs*McGee on 2009-06-25
> Have you been able to see during startup if the cd/dvd rom drive has been identified?

Not that I noticed... when and where would I look for an indication?

---

### Post by khelben1979 on 2009-06-25
> **Noobs*McGee said:**
> Not that I noticed... when and where would I look for an indication?

When the Linux system boots up for the first time. 

All log messages is stored in /var/log, but I don't know exactly in what file you should look in at this time.

---

### Post by Noobs*McGee on 2009-06-25
> **khelben1979 said:**
> When the Linux system boots up for the first time. 

All log messages is stored in /var/log, but I don't know exactly in what file you should look in at this time.

Do you mean when the OS itself first loads (after the system locates the boot directory) or when I first log into Ubuntu?  I'm not exactly a tech guru, so you might have to dumb things down a little bit more for me to follow along...  I apologize


Edit: I found the /var/log folder, and there's a ton of stuff in there... can you give me a better idea what I should be looking for?

---

### Post by khelben1979 on 2009-06-25
> **Noobs*McGee said:**
> Do you mean when the OS itself first loads (after the system locates the boot directory)

Yes!

> **Noobs*McGee said:**
> Edit: I found the /var/log folder, and there's a ton of stuff in there... can you give me a better idea what I should be looking for?

No.

---

### Post by mc4man on 2009-06-25
Run this to see if drive is recognized
```
sudo lshw -C disk
```
or```

grep "CD-ROM" /var/log/dmesg
```

To ck .on any dma or related issues

```
grep "UDMA" /var/log/syslog
```
or
```
grep "UDMA" /var/log/dmesg
```
if you run the sudo lshw ... with a dvd in the drive that could show  some add. info

---

### Post by Noobs*McGee on 2009-06-26
Okay, so here's what I get when booting up (everything after the Toshiba logo startup screen disappears):


GRUB Loading stage1.5.

GRUB loading, please wait...
Press 'ESC' to enter the menu...

Boot from (hd0,0) ext3     [long string of alphanumerics]
Starting up...
[     2.520070] IO APIC resources could not be allocated.
Loading, please wait...


Then the Ubuntu loading screen comes up followed by the Login screen.



And when I enter ```
sudo lshw -C disk
``` into terminal I get this output:

  *-disk                  
       description: ATA Disk
       product: TOSHIBA MK1032GA
       vendor: Toshiba
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: AB21
       serial: 65FO2824S
       size: 93GiB (100GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=13731372


Additionally, ```
grep "CD-ROM" /var/log/dmesg
``` returns no output.


```
grep "UDMA" /var/log/syslog
``` returns a very long output, which I will post if you think it will help, but for now I will refrain.


And finally, ```
grep "UDMA" /var/log/dmesg
``` gives the following output:

[    2.113418] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1100 irq 14
[    2.113421] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
[    2.276447] ata1.00: ATA-6: TOSHIBA MK1032GAX, AB211A, max UDMA/100
[    2.284465] ata1.00: configured for UDMA/100


I honestly have no idea what any of this indicates, so if this tells you anything, please let me know.

---

### Post by mc4man on 2009-06-26
What it all shows is no cd/dvd drive has been found.
You should identify your hardware and search for any hardware specific 'no cdrom detected' issues and possible solutions. (usualy a bios edit, update or a kernel boot parameter.

If nothing specific found then look for generic no cdrom detected threads and possible fixes.

This will show a fair amount (look in home folder for file

for a html file (very readable	
```
sudo lshw > hardware -html
```

or if preferred a text file 

```
sudo lshw > hardware 
```

---

### Post by Noobs*McGee on 2009-06-26
Well, just for ***** and giggles, I decided to try and pop in the Ubuntu Live CD and see what happened when I tried to boot to that... and it worked fine, which indicated to me that there is nothing wrong with my drive and it must be an issue with Ubuntu.  So I booted up normally again and - again, just for ***** and giggles - decided to pop in one of my DVDs (that hadn't worked previously) and lo and behold, the disc was recognized :popcorn:!!  A little icon popped up on the desktop and I got a prompt asking if I wanted to play the DVD with MPlayer and everything! :D

So yeah, I have no idea what booting to the live CD did, but for whatever reason it seems to have fixed my problem.  I'm still having some issues with MPlayer not being able to play the content of the DVD and VLC not playing it properly, but I think that is a seperate problem due to the format of the data on the disc (it is a backup copy of "Batman Begins" that I made a while ago on WinXP using DVDShrink).  I'm sure I can find a solution to that problem elsewhere in the forums...  Other than that though, everything seems to be working fine.  I even just finished burning a DVD using Brasero :razz:.

Anyway, thank you for all your help.  It may not have provided a direct solution (I'd really like to know why the Live CD thing worked :-k), but it did enlighten me to a lot of useful troubleshooting techniques and I really appreciate you taking the time to respond regardless.  It's people like you that make the Ubuntu Community worth being part of :KS

---

### Post by Noobs*McGee on 2009-06-30
...and once again, it's not working :roll:

Really wish I knew what fixed it last time... guess I'll have to try the booting-to-live-cd trick again... this is going to get old quickly ](*,)

---

### Post by pndragon on 2009-06-30
I'm having a similar problem trying to read backup data dvds from a desktop that I am about to switch over to kubuntu from winXP... my laptop doesn't even register them. This could be a serious problem as some of them are family pics and records.

---

### Post by Noobs*McGee on 2009-06-30
So, the Live-CD fix didn't seem to work this time...:-k  I'm guessing this means there's some sort of problem with my hardware - bad connection, or what have you.  I don't think it's a major problem, because the drive spins up normally and isn't making any unusual sounds or anything.  I have noticed that the drive will sometimes make a noise  when it is not in use as though you had just put a disc in, usually when the laptop itself is moved or the screen is tilted.  This further leads me to think it is a connection problem.  I guess I'll have to have someone who knows a little more about the innards of computers than I to take a look and fix the problem if there is one...  (I'm really hoping it is just a connection problem, because at least I will know what the problem is)

---

### Post by Noobs*McGee on 2009-07-02
Just to update:  I ended up taking my drive out to have a look at the connection terminal/clean it up, and I think I found the source of the problem - there was a large piece of dust/lint hanging off the connection terminal (on the drive) and probably more inside the drive bay (where the drive plugs into the connection port).  This laptop is almost 4 years old, and this is the first time I've opened her up to clean inside, so I guess it's not surprising she's got some dust built up in her hard to reach places ;).

Anyway, I cleaned her out pretty good with some compressed air, put the drive back in and booted back up, and the drive seems to be working properly now.  I'm hoping this was in fact the source of the problems, and that it's a permanent fix [-o<...

I'm still having some playback problems however, which I'm assuming are unrelated.  But I guess I will start a new thread about that, since it is a separate topic.

Anyway, just wanted to clear things up.  I will report back if the problem returns :)

---

