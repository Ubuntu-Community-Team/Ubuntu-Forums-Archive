---
title: "Help!! Can't log in! I'm dead!"
date: 2005-12-10
forum: General Help
---

### Post by John Jason Jordan on 2005-12-10
Started using Ubuntu64 with Hoary last summer after getting a brand new Compaq R3240 laptop with AMD64. Recently upgraded to Breezy.

Until a couple days ago I could not find a way to make a backup. If something was critical I would manually copy it over my home ethernet to this Windows 2000 computer. I was trying to make backups to an external USB drive hanging on the Windows 2000 computer. But it seemed impossible to get the syntax right to get any backup utility to use that drive, even though Konqueror and Nautilus can see it and write to it easily. Eventually I bought a new portable pocket 60 Gb external USB drive that is now directly on the laptop.

Subsequently I made a backup from / to this drive using Dump. The archive file is still there. A friend at a local LUG showed me how to do it with Dump.

Yesterday I was reading in these forums and discovered that someone was using Kdar to make backups. Using Synaptic I installed it. I had to launch it from the command line because it did not install a menu item under Applications in the panel.

After fiddling with it for a bit (its help files are missing) I managed to get it started making a backup to the new USB drive. After about 40-50 seconds it locked up the computer completely. Mouse, keyboard, everything dead and the CPU monitor said it was running at 2GHz. Something had gone into an endless loop.

There was no choice but to hit the power button. When I restarted the computer everything came back as before. I tried running Kdar again. This time it ran for about 25-30 minutes before it locked up the computer. Again I had to hit the power button to get out of it.

When I restarted the usual login screen came up. I entered my username and password as I always do. But instead of logging me in it popped up a message that there was no user account for me (jjj). I tried all the options, but the only way I could get logged in was with Failsafe Terminal. That opened a little square window in the lower right corner of the screen (evidently X was running). From there I can su to root, but I am stuck because I have no idea what needs to be fixed.

As luck would have it I was at a local Linux user group meeting the other night. Ubuntu is popular with this group. One of the members had some sets of CDs, including the live/install set for 64-bit. I brought one home, thinking I would probably never need it but might end up giving it to a friend.

So after this morning's disaster I put in the live CD. It booted just fine. It also sees the external USB drive with the archive file created by Dump two days ago. That's the good news. The bad news is that it cannot see the filesystem on the computer's hard disk. Therefore I can't use it to correct whatever is wrong, even if I knew what to fix (which I don't).

Then I tried the Install CD, thinking that it might have a Repair utility. It does not (or at least I couldn't find the option). It appears that it would happily go ahead and reinstall Ubuntu, but I suspect that will wipe out all my files and all my settings, installed programs, etc.

It seems the best route for me would be to Restore from that Dump backup file. Unfortunately, I've been googling on how to do that and none of the instructions are in a version of English that is comprehensible to me. Like I have no idea what they are talking about. Maybe if I had a degree in computer science I could figure it out, but I don't.

Any suggestions welcome. I'm seriously dead here. :(

---

### Post by aysiu on 2005-12-10
[QUOTE=John Jason Jordan]
So after this morning's disaster I put in the live CD. It booted just fine. It also sees the external USB drive with the archive file created by Dump two days ago. That's the good news. The bad news is that it cannot see the filesystem on the computer's hard disk. Therefore I can't use it to correct whatever is wrong, even if I knew what to fix (which I don't).[/QUOTE] It won't *automatically* see your computer's hard drive and *automatically* mount it (Knoppix will, but not Ubuntu's live CD), but you can still *manually* mount it.

Pop the live CD in and post the output of these commands ```
sudo fdisk -l
df -h
cat /etc/fstab
``` I can help you get it mounted so you can see what's going on (Is your user account full? Does it really not exist?). I don't know what you should do after that, though.

---

### Post by John Jason Jordan on 2005-12-10
[QUOTE=aysiu]It won't *automatically* see your computer's hard drive and *automatically* mount it (Knoppix will, but not Ubuntu's live CD), but you can still *manually* mount it.

Pop the live CD in and post the output of these commands ```
sudo fdisk -l
df -h
cat /etc/fstab
``` I can help you get it mounted so you can see what's going on (Is your user account full? Does it really not exist?). I don't know what you should do after that, though.[/QUOTE]

OK, here is what I got:

ubuntu@ubuntu:~$ sudo fdisk -l

-----
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7296    58605088+   c  W95 FAT32 (LBA)

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         125     1004031   82  Linux swap / Solaris
/dev/hda2   *         126        7296    57601057+  83  Linux
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/casper-snapshot
                      2.0G  1.4G  577M  70% /
tmpfs                 626M  4.0K  626M   1% /dev/shm
tmpfs                 626M   14M  613M   3% /lib/modules/2.6.12-9-amd64-generic/volatile
tmpfs                 626M   12K  626M   1% /tmp
tmpfs                  10M  2.9M  7.2M  29% /dev
/dev/sda1              56G   11G   43G  20% /media/usbdisk
ubuntu@ubuntu:~$  cat /etc/fstab
/dev/mapper/casper-snapshot / auto noatime 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/hda1 swap swap defaults 0 0
ubuntu@ubuntu:~$
-----

So apparently it is able to see the computer's hard disk. But if I give it mount /dev/hda2 it gives me:

ubuntu@ubuntu:~$ mount /dev/hda2
mount: can't find /dev/hda2 in /etc/fstab or /etc/mtab

Not sure what to do next.

---

### Post by aysiu on 2005-12-10
```
sudo mkdir /save_my_ubuntu
sudo mount -t ext3 /dev/hda2 /save_my_ubuntu
gksudo nautilus
``` Then go to /save_my_ubuntu

---

### Post by John Jason Jordan on 2005-12-10
[QUOTE=aysiu]```
sudo mkdir /save_my_ubuntu
sudo mount -t ext3 /dev/hda2 /save_my_ubuntu
gksudo nautilus
``` Then go to /save_my_ubuntu[/QUOTE]
OK, that worked. Nautilus is open with save_my_ubuntu open. save_my_ubuntu appears to have the whole filesystem in it -- even my home folder and all my files.

Next, now that I'm in the filesystem, I suppose I need to fix something. My user account?

---

### Post by aysiu on 2005-12-10
[QUOTE=John Jason Jordan]
Next, now that I'm in the filesystem, I suppose I need to fix something. My user account?[/QUOTE] I don't know.

Since apparently "jjj" didn't exist, maybe pop into /home/jjj to see if it's there. If it is... I don't know. If it isn't, that's weird, but that's also probably what the problem was.

---

### Post by John Jason Jordan on 2005-12-10
[QUOTE=aysiu]I don't know.

Since apparently "jjj" didn't exist, maybe pop into /home/jjj to see if it's there. If it is... I don't know. If it isn't, that's weird, but that's also probably what the problem was.[/QUOTE]
Everything appears to be there, including my home folder 'jjj' and all the files and subfolders in it.

But does Linux keep user login information in the user's home folder? Maybe it's just the login that is broken.

---

### Post by aysiu on 2005-12-10
[QUOTE=John Jason Jordan]Everything appears to be there, including my home folder 'jjj' and all the files and subfolders in it.

But does Linux keep user login information in the user's home folder? Maybe it's just the login that is broken.[/QUOTE] You're probably right. Unfortunately, I don't know much about that...

---

