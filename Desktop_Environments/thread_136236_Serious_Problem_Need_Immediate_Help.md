---
title: "Serious Problem Need Immediate Help"
date: 2006-02-25
forum: Desktop Environments
---

### Post by kirby_t07 on 2006-02-25
Hello everyone, i installed ubuntu on my laptop today after finally completing months and months worth of essays. These are extremely important essays, i have backed up versions but they are not finished and i cannot re-write them as i dont have time. my problem is that ubuntu will not startup and therefore i cannot access my disk, i get the following error on starting up;
EITHER:
*setting up networking
/etc/rc2.d/s99 fetch mail: line 23:awk:command not foundund/Power-funcs:no such
OR
Starting system log daemon...d: command not found not found

Windows xp, which is setup to dual boot with will not work either.
I really ened to get some kind of os running asap so please anyone who can help me please do. xp just gives me the blue screen and no options so ubuntu seems to have some hope of booting, it managed to boot once, then on the second time i restarted it it gave me these error messages, i did not configure the network, could this be part of it? im trying live cd as we speak, and on the grup menu it gave me a thing called memory test so im running that to see if it can achieve something. 
:( PLEASE HELP
excuse caps and type-o's i really need this sorted

---

### Post by kirby_t07 on 2006-02-25
Me again, i have got ubuntu live running with no problems, but the partitions are not showing up, this is normal because they didnt run before when i did live either, anyway i can access them? im considering a bootable cdrom like bart-pe but i dont have a cd-writer, i could get a friend to burn it for me though. please reply people!

---

### Post by bscbrit on 2006-02-25
Can you still boot ubuntu in recovery mode?

---

### Post by claes on 2006-02-25
[QUOTE=kirby_t07]Me again, i have got ubuntu live running with no problems, but the partitions are not showing up, this is normal because they didnt run before when i did live either, anyway i can access them? im considering a bootable cdrom like bart-pe but i dont have a cd-writer, i could get a friend to burn it for me though. please reply people![/QUOTE]

You can mount the partitions manually and try to copy the files to another machine if you have network support with the live cd.

Try this command and look for your ubuntu partition:

sudo fdisk -l /dev/hda

Disk /dev/hda: 40.0 GB, 40007761920 bytes
16 heads, 63 sectors/track, 77520 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1938      976720+  82  Linux swap / Solaris
/dev/hda2   *        1939       15501     6835752   83  Linux
/dev/hda3           15502       77520    31257576   83  Linux

Thatäs what it looks like for me. I have a swap partition /dev/hda1 and my root file system is on /dev/hda2 and I have partitioned /home on /dev/hda3.

If I would like to access /home from my ubuntu installation I simply use:
sudo mount -t ext3 /dev/hda3 /mnt

And then I can access the files in the /mnt directory.
You might have to change the filesystem type if you choose another filesystem during the installation if not this should work.

Claes

---

### Post by smittyfree on 2006-02-25
Wow that's scary, makes me glad I keep all my files in triplicate.

---

