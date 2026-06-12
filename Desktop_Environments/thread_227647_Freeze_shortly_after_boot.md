---
title: "Freeze shortly after boot"
date: 2006-08-02
forum: Desktop Environments
---

### Post by Admiral Frosty on 2006-08-02
Here's a puzzler for you:

I've got a computer that has, up until the last couple of days, been fine. Due to a windows virus, I reformated the whole drive and started from scratch (It was nasty). I tried to backup my linux files with two different live CD's, Knoppix and Overclockix, both of which have worked before. They both bailed-out on boot with kernal panics. 

So I decide to part with my files and wipe it anyways, with a fresh copy of Ubuntu 6.06 in it's place. *That* freezes while loading the live desktop, but works after a reboot. Installer freezes a couple of times, but less so when I don't use a FAT partition. 

I make it though the installation and am sitting at a fresh desktop. Now I am *still* experiencing random freezes, some while booting, others at desktop, all of them happen within minutes of booting. I haven't used it more then a five minutes, tops without a freeze.


My hardware has not changed, and I have ruled out thermal issues and a bad hard drive. Memtest86 turns up nothing. It happens after a clean install and on live disks, so I suspect a hardware issue. I am running: a Nforce 2 motherboard, Athelon XP 2400, Asus GeForce 6800, and a NIC (whose maker escapes me), and a Antec 500 watt PSU.

Thanks for any insight you can offer!

---

### Post by fourchannel on 2006-08-02
hrm... not sure why, but if you *really* want to wipe it down to where you scrape the paint off the harddirve then here's what I would do to completely excorsize a computer.

1. Download a copy of System Rescue CD
2. check bios and make sure that primary/slave setup for IDE's are correct
3. launch the Sysrescd and type dban for the boot prompt.
4. use a 3 pass wipe and reboot the system at 35% complete. (in my experience you don't have to scramble the harddrive more than once to corrupt the data)
5. reboot the computer and boot the system rescue cd normally (just press enter at boot prompt)
6. use fdisk to setup partitioning the way you want it. Like an ext3 partition for /, a swap partition that is at least twice as big as the amount of ram in your computer, and a /boot if you want. It's not really nescessary.
7. find another computer to use, cause this will take a *while* but should ensure an integral partition.

run these commands. They actually make the filesystems however they check the harddrive for badblocks, which is a lot slower but I have had drives with a ton of bad sectors perform error free after I setup the filesystem to skip the bad blocks.

assuming that /dev/hda1 is your main partition, the one used for /
and that /dev/hda2 is your swap partition, then change these commands accordingly to your setup.


```
mkfs.ext2 -j -cc -v /dev/hda1
``` > This being the ext3 partition for your main data. Yes, the command is mkfs.ext**2** but the **-j** option sets it to ext3.

```
mkswap -c /dev/hda2
``` this is your swap partition.

After both partitions have been correctly built, restart and use the Ubuntu 6.06 install cd. **when it gets to the point of setting up partitioning, go manual and tell it **do not format, keep existing data** when using partitions.** that is not an option with swap so don't worry about it.

For a bit of reference. I have a 250G harddrive and it took like 36 hours to create the partition. But I have had no problems whatsoever with losing data, bad sectors, corrupted fs's, you name it.

---

### Post by Admiral Frosty on 2006-08-02
Oops, System Rescue gave me a kernal panic: ```
<0>Kernal panic - not syncing:Fatal exeption in interrupt
```

...So I reset my bios back to default. Now it boots! I think the problem was there. I'll still go though the rest of the formating, as it sounds like a good idea anyway (I already did dban from a floppy).

Thanks!

---

### Post by Admiral Frosty on 2006-08-02
I spoke too soon. It froze while reinstalling Windows (I install windows first, linux second, so as to not mess up grub). For reference, this is the first time ever that the XP installation has froze like that on me. 

I'm begining to wonder if it's my IDE cables or something silly like that...

---

### Post by fourchannel on 2006-08-02
It could definately be the cables. In past times I've had things like this happen due to:

1. cpu is a little too overclocked
2. cables are bad/loose
3. jumpers on the drives are not setup for Master/Slave correctly
4. Harddrive gets too hot
5. Bad power supply fried the mobo
6. Power supply is under powered. (this usaully is a problem when playing graphics intensive games)
7. dust in the CD laser
8. the CPU is loose in the socket, needs to be taken out and placed back in
9. the bios needs to be upgraded.
10. and bad RAM, but you said you already ran memtest86 - so this is probably not it. =D

I think you have a hardware problem most likely. Post back with what you find out. I'm sure we can figure this out.

---

### Post by Admiral Frosty on 2006-08-03
Well, after ruling out all software issues, I started to remove my hardware, one piece at a time. The first thing I take out is my NIC, and 'voila! It works! What ever was wrong with it was *very* wrong.

Thanks for your input, fourchannel!

---

