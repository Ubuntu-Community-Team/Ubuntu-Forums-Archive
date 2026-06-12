---
title: "Machine locks up when copying lots of files"
date: 2009-04-21
forum: General Help
---

### Post by AboveTheLogic on 2009-04-21
Hi All-

I've been racking my brain on this issue. I gave up running a software raid1 in lieu of simply doing incremental backups of important data to one of the three 1TB drives I have installed in my system.

The problem I'm running into now is when I try to copy a lot of data from one SATA drive to another, the machine will lock up and needs a hard reset.

Originally I was trying to copy all of ~800GB of data from one drive to another and it locked up, but last night when trying to copy about 20GB of data it locked up then as well.

I've tried with the Thunar file manager as well as simply opening up a terminal and running "cp -rv /mnt/1TB/* /mnt/backup" command, both with the same results.

It is a MSI P45 NEO-F motherboard with the SATA mode set to ACHI (not IDE), more specs in my signature. DVD+RW DL on SATA 1, and 1 TB drives on SATA 2, SATA 3, and SATA 4. OS is on a 160GB drive on IDE master, and there is another 750GB Data drive on IDE slave (only 1 IDE port, no secondary).

OS is Mythbuntu 8.10 with kde-core installed for access using FreeNX. I've tried with both the console user (myth tv which loads XFCE I believe) and my other user through FreeNX which loads KDE.

I'm not exactly sure what is causing the problem. I'm thinking of going so far as to mapping both volumes as network drives from a windows box via samba and copying then, maybe that will take some load off of the box and keep it from locking up (although the copy will take a very long time). I'm also wondering if this is contributing to the issues I was having with making RAID work properly.

Any input is appreciated. Thanks!

---

### Post by fjgaude on 2009-04-21
Try taking the TV board out and see if it still does the same thing.

---

### Post by AboveTheLogic on 2009-04-21
OK, I actually have 3 tuners... USB ATSC, PCI ATSC, and PCI DVB (I'll update the sig).

Is it possible for me to disable them somehow instead of removing them? This machine is kinda of a pain to get to. If not I'll do what I gotta do...

---

### Post by juancarlospaco on 2009-04-21
run it niced

---

### Post by AboveTheLogic on 2009-04-21
> **juancarlospaco said:**
> run it niced

what does that mean?

---

### Post by fjgaude on 2009-04-21
Niced? means to give the cards low priority with something like System Monitor. I would thing the real way is to actually physcially remove these cards from the PCI bus or however they are connected.

But these large file transfers are a pain... likely something is not well-behaved with taking over the CPU cycles and then letting them go.

You could file a bug report. <smile>

---

### Post by AboveTheLogic on 2009-04-21
I thought about messing with prioiries but am unsure how to do that. I've looked at system monitor and don't really see how to change the priorities but will play around with it a bit more.

I'd like to simply be able to copy the files and have the file copy itself have the lower prioirty. The machine is a home theater PC so the cards should be at a high prioirity if anything... I just run some background processes as well (torrents, ssh, proxy, etc...).

I'm still not sure why removing the tuner cards would help but I'll definetely give it a shot (not sure when, maybe tonight or tomorrow), but I would much prefer a different solution of course, because those cards will just go right back in.

---

### Post by fjgaude on 2009-04-21
Really, one way to trouble-shoot something is one-at-a-time remove things until the issue goes away. Then you know something you didn't before.

That's the only way I know how to debug things...

---

### Post by Yashiro on 2009-04-21
Use rsync to do it instead, but it sounds like you have a bit of an issue, yeah.

---

### Post by AboveTheLogic on 2009-04-21
haha

yeah I intended to use something like rsync, but yeah... gotta get this issue fixed 1st

I probably won't go removing parts until the weekend, but I'll report back

thanks

---

