---
title: "Dapper Performance - Is this normal?"
date: 2006-07-10
forum: Desktop Environments
---

### Post by richardq on 2006-07-10
I'm running Dapper on a P4-3Ghz machine with 1GB Ram. I've given it a 3GB swap partition.

When running Gnome, nothing open on the desktop except system monitor - I'm getting 6% CPU usage. I think this is reasonable, but tell me if I'm wrong.

But the weird thing is that when I launch any app, the system monitor goes to 100% CPU usage (no swap file usage at all) for 5 to 10 seconds before the app actually appears. Is it normal for the system to top out like that every time I launch an app? 

During normal use, I find that the CPU usage jumps around quite a bit, but apps like Firefox (swiftFox actually), Gedit and Terminal are all sometimes stalling for several seconds every once in a while during which time the CPU usage is flatlined up at 100%.

I've got prelink loaded as well. It seems like this system is not running as efficient as it should be. I've tried running Xubuntu with very similar results (no marked improvement).

---

### Post by vem0m on 2006-07-10
which kernel are u using?

---

### Post by richardq on 2006-07-10
> **vem0m said:**
> which kernel are u using?

I'm running the 2.6.15-25-686 kernel.

---

### Post by vem0m on 2006-07-10
which way did u install it? E.G guide? or method/program used?

---

### Post by richardq on 2006-07-11
I have two 160GB drives each containing an NTFS partition. I installed linux onto the first drive (sda) and put my /home partition on the second drive. Here's the fstab file listing:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0 
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb2       /home           ext3    defaults        0       2
/dev/hdb1       /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1 
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda6       /osshare        vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda5       none            swap    sw              0       0 
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

I installed using the dapper-alternate 386 iso (not the live CD).  I was having trouble when pre-configuring the partitions with Partition magic from Windows so instead I decided to delete those partitions and do everything from the Ubuntu installer partitioner. 

I have installed AIGLX but the benchmarking I've done on app launching times has shown that things are actually launching quicker with AIGLX than with Metacity. 

Oh. Also I am getting the 'HAL failed to Initialize' message on bootup to the desktop. I've posted elsewhere regarding this, but have seen no response. I'm not sure if that has anything to do with it.

---

### Post by vem0m on 2006-07-11
i mean which way did u install the i686 kernel?

---

### Post by richardq on 2006-07-11
> **vem0m said:**
> i mean which way did u install the i686 kernel?

Hehe, sorry. 

I installed the kernel at the terminal with 'apt-get install linux-686'.

---

### Post by d0gi on 2006-07-11
I'm seeing a lot of similar threads here. I have the same problem now using 2.6.15-26-686. There's also some lag when typing in gnome-terminal :-? Didn't happen in 2.6.15-20-686.

---

### Post by vem0m on 2006-07-11
i am about to update kernel at next reboot will let u know if anything goes wrong

---

### Post by JoWilly on 2006-07-11
This is definitely not normal. Your system should be very fast (I had a P4 3gz with 1Gb ram a few month ago).

Is there any difference just after a fresh install, without your tweaks (prelink, aiglx ,etc...) ?

When you have system monitor open and watch the cpu usage, what process is taking 100% cpu ?

PS: just FYI, your 3 Gb swap is definitely not needed (unless you are using heavy imaging/video apps working with very large files. 500Mb should be more than enough for normal operation. On my P4 with 1Gb I had always no swap for years, no need for it (and I was making heavy use), so if you put 500Mb swap you will see that you hardly reach 25Mb swap usage

---

### Post by richardq on 2006-07-11
> **JoWilly said:**
> 
Is there any difference just after a fresh install, without your tweaks (prelink, aiglx ,etc...) ?

When you have system monitor open and watch the cpu usage, what process is taking 100% cpu ?

I kept an eye out for this after doing my fresh install and I was getting similar behaviour right at the start. If anything, the system is more responsive (slightly) with aiglx and prelink.

Watching the system monitor, it appears that no matter which app I launch (I've tried Gedit, GCalc, Terminal, Firefox, Gnometris and Epiphany), the CPU usage goes up to 100% for about 5 to 15 seconds and then the app appears and the usage immediately falls back to 10% or so. I get a similar delay when launching Nautilus as well. Opening file->open dialog boxes are quicker and take about 1 full second to appear. 

> **JoWilly said:**
> PS: just FYI, your 3 Gb swap is definitely not needed (unless you are using heavy imaging/video apps working with very large files. 500Mb should be more than enough for normal operation. On my P4 with 1Gb I had always no swap for years, no need for it (and I was making heavy use), so if you put 500Mb swap you will see that you hardly reach 25Mb swap usage

Thanks for the info. I am assuming I could resize the swap partition without screwing up anything else?

Also, do you think the 'HAL initialization failure' that I'm seeing at bootup has anything to do with it?

---

### Post by JoWilly on 2006-07-11
> **richardq said:**
> I am assuming I could resize the swap partition without screwing up anything else?

Also, do you think the 'HAL initialization failure' that I'm seeing at bootup has anything to do with it?

Yes, you can resize the swap.

As you say, the problem "could" be linked to the hal failure. I suggest you report a bug on launchpad (search first) to inform the developers so they can start doing something about this. Don't forget to put you complete system specs (motherboard, etc...).

---

### Post by richardq on 2006-07-14
I think I've fixed the problem.

I installed the linux-686-smp package to upgrade the kernel and the apps now launch quickly. I had previously upgraded to the non-smp package. I have a Hyperthreading processor so maybe I needed the smp package to make use of it? Not 100% sure really.

---

### Post by vem0m on 2006-07-14
yes i believe that is correct :)

---

### Post by Daniel15 on 2006-07-14
> . I have a Hyperthreading processor so maybe I needed the smp package to make use of it
So what's this smp thing? Is it related to HyperThreading?

> On my P4 with 1Gb I had always no swap for years, no need for it 
Heh, my server running Ubuntu Linux (server edition) has half of its 256 MB RAM in use, and 0 KB of the 200 MB swap in use :P

---

### Post by richardq on 2006-07-15
> **Daniel15 said:**
> So what's this smp thing? Is it related to HyperThreading?


According to the description in Synaptic for linux-686-smp:

[I]Complete Linux kernel on PPro/Celeron/PII/PIII/PIV SMP.
This package will always depend on the latest complete Linux kernel available
for Pentium Pro/Celeron/Pentium II/Pentium III/Pentium IV with SMP support.
SMP (symmetric multi-processing) is needed if you have multiple processors.
[/I]
I read a post here on the forums about picking the right kernel and it said that the smp package would be for newer Pentium chips with HT or dual core systems. I definitely don't have multiple processors but I do have HT.

---

### Post by richardq on 2006-07-15
Aaaargh... Upon bootup this morning, the machine was back to it's old slowness as far as application launch. I then marked linux-686-smp for reinstallation in synaptic and then restarted the system when it was done. To my amazement apps loaded quickly once again. 

However, after happily installing a few other apps (F-spot and some python editors) I restarted the system just to check if the speed would stay. It did not. And now I've tried everything I can think of regarding kernel upgrades and it doesn't seem to help.

One thing I notice now: Once I have opened one terminal window (which takes about 11 seconds), if I open a second one, it appears within 3 seconds. If I close them both and open a new terminal window, it again takes 11 sec. This same behaviour goes for gedit windows as well. Once I have started the app, new windows appear much quicker.

I have run strace on gedit and gcalctool. This is a small portion of the strace file created when I launched gedit:

```
execve("/usr/bin/gedit", ["gedit"], [/* 31 vars */]) = 0
uname({sys="Linux", node="ubuntu", ...}) = 0
brk(0)                                  = 0x80db000
old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f23000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
old_mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f21000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=46968, ...}) = 0
old_mmap(NULL, 46968, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f15000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/liblaunchpad-integration.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@\245\3"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=12752, ...}) = 0
old_mmap(0x41039000, 13408, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x41039000
old_mmap(0x4103c000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x4103c000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libgtksourceview-1.0.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\200\236"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=179468, ...}) = 0
old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f14000
old_mmap(0x4103f000, 180088, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x4103f000
old_mmap(0x4106a000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2a000) = 0x4106a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libgnomeui-2.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\360h2B"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=544256, ...}) = 0
old_mmap(0x4230d000, 544372, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x4230d000
old_mmap(0x4238e000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x80000) = 0x4238e000
close(3)                                = 0
```

The access(... to close(3) pattern repeats at least 50 or 60 times near the start of the file. Each time it's opening a different library, but the /etc/ld.so.nohwcap part appears each time as well and I'm not sure if it should.

I read somewhere that using 'touch /etc/ld.so.nohwcap' sped things up for some others, but I don't even have this file, so the touch command just generates a file missing error.

It seems like it is loading some libraries very slowly or having trouble find them maybe? I'm not sure how to test if it's strictly a GTK2 thing.

Just about every app I run on here is launching slowly, but I just noticed that launching xmms is fast! And launching the IDLE python editor is relative fast (under 2sec).  Maybe they're both not GTK based programs?? 

Anybody got any clues about this?

Also, one other thing. Doing an apt-get dist-upgrade tells me that the gnome-session and libwnck18 packages are being kept back and then lists 2 packages not upgraded. Maybe this is related?

---

### Post by JoWilly on 2006-07-16
Try to reinstall these packages (gnome-session and libwnck1) with synaptic.

Do you still have the problem with hall not starting ? Was hal starting when everything was fine ?

I don't have that file on my sstem either (/etc/ld.so.nohwcap).

Have you posted a bug report with al your details on launchpad ?

---

