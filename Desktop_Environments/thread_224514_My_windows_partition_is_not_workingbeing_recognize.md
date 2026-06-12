---
title: "My windows partition is not working/being recognized properly"
date: 2006-07-28
forum: Desktop Environments
---

### Post by fapapa on 2006-07-28
Up till a few days ago I could dual-boot between Ubuntu and win without a hitch. I had my win partition on hda1 and my Ubuntu partition on hdc1. My setup was such that ntldr was my boot loader and allowed me to choose Ubuntu as well. 

Then I got my Ubuntu live-cd that I ordered and wanted to go through that setup just for the experience. My /home directory is on a seperate partition (hdc5), and I didn't mind having to re-install all my programs, so I went ahead with it. Everything went well except that it wiped out my ntldr and replaced it with grub without asking. To be honest, I hadn't gone into win since then (for obvious reasons :). Today I decided that I wanted to make an image of my Ubuntu '/' partition (hdc1) so that I could just restore from that if I was ever in a jam (with all my progs installed, etc.). I have extra space on hda1, so I wanted to to use gparted to make an ext3 partition from it to then create a massive tarball of hdc1 (a process described elswhere on this forum). Well, when I tried to shrink hda1 and make hda2 out of the new space, after a long (3-4 min) wait of nothing happening, I got an error from gparted saying that the operation did not complete. From that point forward, gparted told me that hda1 is 'unkown' filesystem, whereas it was recognizing it properly as ntfs before that. Now, when I try to boot into windows through grub I get this:

```
Booting 'Windows XP' . . .

root (hd0,0)
  Filesystem type unknown, partition type 0x83
savedefault
makeactive
chainloader+1

Error 13: Invalid or unsupported executable format

Press any key to continue . . .
```


Pressing a key brings me back to my OS choices in grub. Since I haven't tried booting into win since ntldr was overwritten by grub, I don't know if this problem is happening because of the Ubuntu re-install or because of the more recent GPartEd error. Either way, I don't really care about windows, but I have data on that partition that I really need. If anybody could help me solve this I would be very appreciative.

Sorry for being so long-winded and round-about. Hopefully I've supplied enough info to help you help me ;)

---

### Post by Acesomeone on 2006-07-28
Ha! I've had the exact same thing happen to me about a month ago! As you, I wanted to resize my Windows disk, too. After that I got a red screen saying the operation had failed. Likewise, from then on, my Windows disk renders as "Unformatted". No way to change that, still trying to figure out what happened.

Yes, I've tried all the classics, like FIXMBR, FIXBOOT, copying over the NTLOADER-file, etc etc etc... Nothing works. From then on I've been in Ubuntu full-time - which isn't a real problem, but I've still got some games I'd like to finish and have my Media Center work again...

Seems like you've run into the same hazards as I did - being that the parted application in the Ubuntu setup is bugged (yep, they know about it).

My condolences :|

---

### Post by ravindran.k on 2006-07-28
oh!! I have been crashing my partiton tables from various versions of linux ..starting suse 5.1.. Can you provide the partition table info here.. we can get a better piciture.. You can try the below commands:
 
#  fdisk /dev/hda 
and then type p...copy the whole thing in screen and send it.. for all partitions..do it for /dev/hdb , /dev/hdc  /dev/hdd .. I know you have only 2 partitions.. hda and hdc but send the info for all 
 
Cheers!!

---

### Post by fapapa on 2006-07-28
ok, here it is:

/dev/hda:
```
The number of cylinders for this disk is set to 4870.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4870    39118243+  83  Linux
```

/dev/hdb
```
Disk /dev/hdb: 1083 MB, 1083801600 bytes
255 heads, 63 sectors/track, 131 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         131     1052226   82  Linux swap / Solaris
```

/dev/hdc
```
The number of cylinders for this disk is set to 1232.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/hdc: 10.1 GB, 10141286400 bytes
255 heads, 63 sectors/track, 1232 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1         676     5429938+  83  Linux
/dev/hdc2             677        1232     4466070    5  Extended
/dev/hdc5             677        1232     4466038+  83  Linux
```

I just noticed that hda1 is showing up as a linux partition there; That is the drive that should be ntfs. Thanks.

---

### Post by fapapa on 2006-07-31
Um, I just noticed that with fdisk I have the option of changing the partition to any kind, including NTFS, which is what it is supposed to be. Should I do that? Can it damage my data even more? What are the chances it will help? TIA

---

### Post by iamhugeinjapan on 2006-07-31
Reformatting the partition as NTFS will definitely wipe all your data regardless of whether it's still actually NTFS or not.

Are you able to see your hda partition from Ubuntu and look for/copy off useable data first?

---

### Post by Jhongy on 2006-07-31
Hopefully one of the experts here will be able to help you fix this - -I just wanted to add that you should avoid making any changes to the disk without careful consideration. There's a chance that it can be fixed by restoring the original partition table.

Of course, data can still be recovered if you format the disk (maybe even if you copy some files to it), but you would be unable to recover the partition in its original state.

---

### Post by misha680 on 2006-07-31
I am certainly no expert, but I have changed partition types in fdisk before (the "t" command I think) and changing the partition type in fdisk for me definitely had no effect on the data (did not "format" the partition or anything, just changes one byte in the partition table itself, not in the actual partition). Given that, however, I cannot guarantee that once you change the partition type, something else would not do damage to it (Windows, etc). However, since you do not currently have a Windows partition you can boot into anyhow, I would suggest giving it a try (just changing the partition type with the t command to ntfs, nothing else).

Misha

---

### Post by ravindran.k on 2006-07-31
Hi fapapa,
 
Please try mount hda1 as ext2/ext3 ..If it mounts fine..that means ur partition has been formatted. Then, you can use a data recovery utility like Easy recovery and try recovering..
 
However, if you are not able to mount as ext2/ext3 , then please chnage the partition id to ntfs type and try mount again as a ntfs partition...and if it mounts.. u can check if its data is present..
 
Lets c ..which options work for you !

---

### Post by fapapa on 2006-07-31
Thanks everybody for the help so far. While the problem is not solved, we definitely have made progress. Mounting as ext3 did not work . . . which means I did not reformat by mistake. So I changed the fs type to ntfs using fdisk and wrote the partition table. Mounting as ntfs still did not work and gave me the usual error message. I did 'dmesg | tail' as per the error message and this time there was something interesting in the log. It said that it did not try to recover from errors because 'errors=recover' was not used. A little digging around in the man pages and I typed this command: 'sudo mount -t ntfs -o errors=recover /dev/hda1 /win'. The drive is now mounted and, from what I can tell so far, all my data is there!!! I even copied over a .txt file and looked at the contents. But, when I try to boot into it, I still get the same error as in my original post. I did another 'dmesg | tail' after remounting and got this:

```
[17179918.648000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17179918.648000] NTFS-fs warning (device hda1): read_ntfs_boot_sector(): Hot-fix: Recovery of primary boot sector failed: Read-only mount.
[17179918.648000] NTFS-fs warning (device hda1): read_ntfs_boot_sector(): Using backup boot sector.
[17179918.704000] NTFS volume version 3.1.
```

As you can see it is mounted read-only and had to use the backup boot sector. I'm guessing that fixing this boot sector in some way (restoring the backup boot sector?) would allow me to boot from it again. Any idea how? Thank you.

---

### Post by andb on 2006-07-31
Try the microsoft knowledge base. WIth the boot cd you can go into the console and there is command or series of commands which do a boot sector restore. Never bothered to find out -exactly- what it did, but that, or something else there might help you.

Given linux support for NTFS (shakey at best), Id be wary of using gparted to resize a ntfs partition, and would have used a comercial product like partition magic instead. If you want to test some partition tools before buying, look for Hiren's boot cd. Big collection of utilities.

---

### Post by ravindran.k on 2006-08-01
> **fapapa said:**
> Thanks everybody for the help so far. While the problem is not solved, we definitely have made progress. Mounting as ext3 did not work . . . which means I did not reformat by mistake. So I changed the fs type to ntfs using fdisk and wrote the partition table. Mounting as ntfs still did not work and gave me the usual error message. I did 'dmesg | tail' as per the error message and this time there was something interesting in the log. It said that it did not try to recover from errors because 'errors=recover' was not used. A little digging around in the man pages and I typed this command: 'sudo mount -t ntfs -o errors=recover /dev/hda1 /win'. The drive is now mounted and, from what I can tell so far, all my data is there!!! I even copied over a .txt file and looked at the contents. But, when I try to boot into it, I still get the same error as in my original post. I did another 'dmesg | tail' after remounting and got this:
 
```
[17179918.648000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17179918.648000] NTFS-fs warning (device hda1): read_ntfs_boot_sector(): Hot-fix: Recovery of primary boot sector failed: Read-only mount.
[17179918.648000] NTFS-fs warning (device hda1): read_ntfs_boot_sector(): Using backup boot sector.
[17179918.704000] NTFS volume version 3.1.
```
 
As you can see it is mounted read-only and had to use the backup boot sector. I'm guessing that fixing this boot sector in some way (restoring the backup boot sector?) would allow me to boot from it again. Any idea how? Thank you.
 
Nice to see some positive results :)  >.Before u try/do anything else...
 
1. MOunt it once again as RO in Linux.
2. COpy your data to the / or /home/<username> . Your data normally will be documents and files in c:\Documents and settings\<Username> on windows. 
3.There are important folders of Outlook maibox, Favorites alll under the above path. If possible copy the direcotyr. Then copy anything else  u might have stored .. maybe c:\Documents and settings\All Users  and c:\Documents and settings\administrator also. 
4. do a search on whole partition guessig the typ eof files u want to recover and copy them as well
5. After all this, I suggest you use a XP Boot cd and boot to recovery console. Boot thru Cd and then option R.
6. Provide admin password when asked. It will say "which windows installaton u want to logon : [1] c:\windows:
7. Run a checkdisk: 
chkdsk /F /V 
8. Reboot and see whether any success.
9. If you dont have xp cdrom, as **_last resort_**, u can :
1. unmount the ntfs.
2. try 
fsck -a
3. remount in rw mode and check . **_You may still need a XP CD to repair XP if this doesnt work, To reinstall XP. so i strongly suggest Step 5_**
 
Pleaese let us all know abt the results..
 
We are too curious =P~

---

### Post by ravindran.k on 2006-08-01
Alsoooo... **DOnt rush to repair the boot sector or MBR yet**... as that may render ur **_Linux unbootable_** and we are not too sure whether you know enough to recover from that scenario.. try only the file system repair and check if Xp boots..
 
_1 more quick Q:_ which boot loader are you using ? GRUB? and where is it installed? /dev/hd(a/b/c/d)(0,1,2,3)

---

### Post by fapapa on 2006-08-01
> **ravindran.k said:**
> Alsoooo... **DOnt rush to repair the boot sector or MBR yet**... as that may render ur **_Linux unbootable_** and we are not too sure whether you know enough to recover from that scenario.. try only the file system repair and check if Xp boots..
 
_1 more quick Q:_ which boot loader are you using ? GRUB? and where is it installed? /dev/hd(a/b/c/d)(0,1,2,3)

LOL, this is too funny . . .
First, thanks for your patience with me.
I followed your instructions to go into repair mode with my slipstreamed XP sp2 cd. The /F /V switches are not available . . . only /P and /R are valid options on my repair console. NEways, running chkdsk immediately reports that there are one or more unrecoverable errors. I did some more poking around and found that even a plain old "dir" didn't work, even though I had the c:\ prompt. So, Ubuntu can see my NTFS files and lets me access them, but microsoft's own recovery console can't. I love Linux more and more every day.

OK, so I hadn't read your second message, saying not to try to repair my MBR. And that's just what I did. It didn't let me boot into windows, but it did, like I've now read, stop me from even booting ubuntu. That's the funny part. No biggy though, I booted from the Ubuntu cd, did some googling and found out how to restore the MBR from the grub> prompt. Only took me about 10 minutes.

As to your question . . . yes, I use grub, but I don't know where it is installed. I guess the default location it would be installed from the live cd installation.

Should I still try to do the fsck -a thing you suggested?

---

### Post by fapapa on 2006-08-02
:D 

All fixed now. For those interested, I booted from my XP CD again and went into the recovery console. This time, instead of doing fixmbr, I used the fixboot command and that did it. Hooray!

---

### Post by ravindran.k on 2006-08-03
Hey fapapa ! Coool ! Enjoy :)

---

### Post by fapapa on 2006-08-07
Just wanted to add a follow up, as suggested by andb. I was brave/stupid enough to try gparted to resize my ntfs partition again, but this time I first did some googling around and found that gparted uses ntfsresize which is supposed to be 99.9% safe. One caveat that is mentioned over and over is defragging the partition before resizing it. That is exactly what I did and it worked beautifully.

Also, if you can't afford to take that 0.1% chance that you'll lose your data, back up first!!!

Perhaps gparted (or ntfsresize) should first check the state of fragmentation and abort with a message telling you to defrag first?

Regardless, it was a good learning experience.

---

### Post by ravindran.k on 2006-08-08
Greetings!
 
Yes. It was indeed a learning experience.. And a chance for others.. Meanwhile, one of my friends tried resizing HFS+(MAC) partiton..but getting "No enough memory" in parted.. This prior to installing Ubuntu..Finally he gave up and repartitioned his HDD as we could not find anyother way!
 
Cheers!

---

