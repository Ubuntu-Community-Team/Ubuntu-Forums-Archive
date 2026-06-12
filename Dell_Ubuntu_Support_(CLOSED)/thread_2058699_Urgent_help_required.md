---
title: "Urgent help required"
date: 2012-09-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by adjbck on 2012-09-16
Hey guys and gals, ive got an urgent problem i need to ask your help for in dealing with. Two - Three years back my mother bought a dell inspirion mini 910 which came preloaded with ubuntu which was great. Except she has no idea what shes been doing. Shes doing a uni dissertation atm and shes been using this to type it up (with no backup) i last saw it running hardy but i remember her saying she had updated so it could be up to maverick atm. 

The problem is when she turns it on it comes up with 

"error: unknown fielsystem.
grub rescue> "

now ive done some digging but all i can find is references to people having used wubi and messing up their grub

id really appreciate all help in this matter as im trying to save her work and its due in less than a week. Thank you for your time

---

### Post by MC_Claus on 2012-09-16
It seems the Master Boot Record has somehow gone missing.

Since you most likely just want the data, have you tried with a live CD/USB stick? If it is just the MBR that has gone missing, the rest of the data might still be there, so you can backup your (moms) data, before trying anything fancy to restore the MBR :)

---

### Post by adjbck on 2012-09-16
@MC_Claus - im currently downloading 10.10 netbook edition. should it be as simple as make a live usb from the iso > boot into ubuntu > host folder and recover data > fresh install of maverick over current one ?

---

### Post by MC_Claus on 2012-09-16
It has been awhile since I messed up my own MBR, but I remember from my dual booting days, that some Windows Updates had overwritten the MBR, thus making dual boot impossible again.

Then I had a live CD/USB stick handy, which enabled me to rewrite the MBR by selecting a certain 'boot from HD' option from the Live CD boot menu.
This is somewhat faster than to reinstall the entire thing, but reinstalling will work too.

Whatever solution you choose, the live CD/USB stick should at least enable you to recover your data.

---

### Post by adjbck on 2012-09-16
@MC_Claus Thank you for your help, i have 17 minutes until the iso has completed downloading (poor internet speeds atm) after which i will create a live usb (5 mins) and let you know the results in possibly just over 30 mins. 

Thank you so very much for your time and patience

---

### Post by MC_Claus on 2012-09-16
No problem, glad to help :)

---

### Post by jrog on 2012-09-16
In case it isn't clear to you from what MC_Claus said, your best (i.e., safest) bet is to use the Live USB to *first *recover/back up any data on the hard drive. I would do this immediately, before attempting to restore the MBR and/or recover the system.

---

### Post by adjbck on 2012-09-16
The live usb has loaded and now in file system i have loads of folders. Where can i locate her data, it was saved on the desktop

---

### Post by MC_Claus on 2012-09-16
> **adjbck said:**
> The live usb has loaded and now in file system i have loads of folders. Where can i locate her data, it was saved on the desktop

It should be found under ~/Desktop, ie /home/[username]/Desktop

---

### Post by adjbck on 2012-09-16
its not there, all thats there is examples and install ubtunu netbook 10.10 .. also i dont have permission to access root

---

### Post by MC_Claus on 2012-09-16
Ah yes right, my bad, the /home/ is of course the live cd's home dir.

You have to mount the drive first. Depending on the live distro there should be an icon on the desktop that should read something in the line of '999 gb' filesystem.

Otherwise try this and post the results:
Press CTRL+ALT+T and write fdisk -l /dev/sda, post results :)

---

### Post by adjbck on 2012-09-16
it wont mount, something about bad sector. i did some research and it looks like its corrupted. it wont even let me download boot repair via terminal. so im downloading ubuntu secure remix which comes with boot repair built in. Hopefully i can repair it from there, if not.. 

well im fresh out of ideas

---

### Post by jrog on 2012-09-16
> **adjbck said:**
> it wont mount, something about bad sector. i did some research and it looks like its corrupted. it wont even let me download boot repair via terminal. so im downloading ubuntu secure remix which comes with boot repair built in. Hopefully i can repair it from there, if not.. 

well im fresh out of ideas
The hard drive could be failing, but you may be able to repair the problems (even if temporarily) and recover data by using fsck on the disk. If you boot the Live USB and open a terminal, you should be able to type "sudo fsck -f /dev/sda1" (but you may have to replace /dev/sda1 with the appropriate partitions for your system) to check and possibly repair the partitions on the disk. Do you know how to see the partitions on your drive? If not, do what MC_Claus suggested earlier: open a terminal and check the output of "sudo fdisk -l /dev/sda" (where /dev/sda is the device name for the hard disk). If you don't understand the output, or you want us to look at it, or something along those lines, just post it (or copy as much of it as you can) here.

The drive should be UN-mounted while you do the above things, so do not mount it when you boot the Live USB.

EDIT: Just a reminder if you don't know: to open a terminal, you can hit CTRL + ALT + t.

---

### Post by adjbck on 2012-09-16
When i type "sudo fsck -f /dev/sda1"  i get the response

fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Filesystem revision too high while trying to open /dev/sda1
The filesystem revision is apparently too high for this version of e2fsck.
(Or the filesystem superblock is corrupt)


The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


"sudo fdisk -l /dev/sda"  gives me 

Disk /dev/sda: 7682 MB, 7682605056 bytes
255 heads, 63 sectors/track, 934 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cb0f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         888     7127040   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             888         934      372737    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5             888         934      372736   82  Linux swap / Solaris

honestly im so confused dude

---

### Post by MC_Claus on 2012-09-16
As jrog suggested your drive might be failing, or close to faling. 

I did a quick Google after the response from fsck, and found this:
[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

Lets try it! :)

Start with
```
sudo fsck.ext4 -v /dev/sda1
```

And lets see the output, if it looks anything like the output from the link i posted (I haven't tried it, haven't had the problem before, so lets take it step by step).

(Another thing you could try is, if you have tried it before and have the 'gear', is to remove the harddrive and put it in a USB tray and connect to another computer)

---

### Post by adjbck on 2012-09-16
@MC_Claus - i tried what you said and this is the reply

 e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Filesystem revision too high while trying to open /dev/sda1
The filesystem revision is apparently too high for this version of e2fsck.
(Or the filesystem superblock is corrupt)


The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by jrog on 2012-09-16
> **adjbck said:**
> When i type "sudo fsck -f /dev/sda1"  i get the response

fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Filesystem revision too high while trying to open /dev/sda1
The filesystem revision is apparently too high for this version of e2fsck.
(Or the filesystem superblock is corrupt)


The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
See what it says at the end there? What is the output of that command? (Type "sudo e2fsck -f -b 8193 /dev/sda1" at the terminal.)

If the above command gives you similar errors, try "sudo mke2fs -n -j /dev/sda1" and report the output.

(The output of your "sudo fdisk -l /dev/sda" is fine; /dev/sda1 is the partition where the data is, so use the commands as written above.)

---

### Post by adjbck on 2012-09-16
I Typed "sudo e2fsck -f -b 8193 /dev/sda1" into the terminal the response was
"e2fsck 1.42 (29-Nov-2011)
e2fsck: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>"

  I tried "sudo mke2fs -n -j /dev/sda1" and it gave me 
"mke2fs 1.42 (29-Nov-2011)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
446160 inodes, 1781760 blocks
89088 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=1824522240
55 block groups
32768 blocks per group, 32768 fragments per group
8112 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632"

---

### Post by jrog on 2012-09-16
> **adjbck said:**
> I Typed "sudo e2fsck -f -b 8193 /dev/sda1" into the terminal the response was
"e2fsck 1.42 (29-Nov-2011)
e2fsck: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>"

  I tried "sudo mke2fs -n -j /dev/sda1" and it gave me 
"mke2fs 1.42 (29-Nov-2011)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
446160 inodes, 1781760 blocks
89088 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=1824522240
55 block groups
32768 blocks per group, 32768 fragments per group
8112 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632"
Great. Try typing this now at the terminal:

sudo e2fsck -f -b 32768 /dev/sda1

Make sure you get the number right. It should begin working through fixing the filesystem. If it does, it is likely you'll want to say 'yes' to all of the questions it asks you.

EDIT: Just to add and hopefully save us some time, if it doesn't work with "-b 32768," try it with one of the other block numbers listed in the last line of the text I've quoted above (from your previous post).

---

### Post by adjbck on 2012-09-16
It asked me to modify around 300 files (i ended up holding down y to speed the process along) should i reboot now? 

Previous to running the command i ran boot repair to survey the system, this is the output
[http://paste.ubuntu.com/1209469/](http://paste.ubuntu.com/1209469/)

---

### Post by snowpine on 2012-09-16
My recommendation is to try and recover the dissertation files (and any other documents you want to keep) before you do anything else.

Then once you have a backup (and better yet, a backup of the backup too!) you can replace the failing drive. I have not used this brand personally, but they enjoy a good reputation from what I've read: [http://www.mydigitaldiscount.com/runcore-pata-mini-pci-e-ssd/](http://www.mydigitaldiscount.com/runcore-pata-mini-pci-e-ssd/)

---

### Post by jrog on 2012-09-16
> **adjbck said:**
> It asked me to modify around 300 files (i ended up holding down y to speed the process along) should i reboot now? 

Previous to running the command i ran boot repair to survey the system, this is the output
[http://paste.ubuntu.com/1209469/](http://paste.ubuntu.com/1209469/)
Good that we're getting somewhere, at least! Yes, reboot. It *may *even let you boot into the OS on the hard drive, though I think that's unlikely. If it doesn't, reboot into the Live USB and try mounting the drive again. It will hopefully work this time. (You may also be able to use Boot Repair to restore grub, but take it step by step.) Try the previous two things (rebooting to the hard drive first, and, if that doesn't work, rebooting into the Live USB and mounting) and let us know what happens.

---

### Post by adjbck on 2012-09-16
> **jrog said:**
> Good that we're getting somewhere, at least! Yes, reboot. It *may *even let you boot into the OS on the hard drive, though I think that's unlikely. If it doesn't, reboot into the Live USB and try mounting the drive again. It will hopefully work this time. (You may also be able to use Boot Repair to restore grub, but take it step by step.) Try the previous two things (rebooting to the hard drive first, and, if that doesn't work, rebooting into the Live USB and mounting) and let us know what happens.

Okay were making a lot of progress, it loaded into ubuntu and i saw the documents on the desktop then in less than a second it froze and this appeared 
 [http://i45.tinypic.com/ejsv0k.jpg](http://i45.tinypic.com/ejsv0k.jpg)

how do i mount sda1 again?
sorry, i used to use ubuntu years ago, haven't touched it since and forgotten everything, just like my French :P

---

### Post by jrog on 2012-09-16
> **adjbck said:**
> Okay were making a lot of progress, it loaded into ubuntu and i saw the documents on the desktop then in less than a second it froze and this appeared 
 [http://i45.tinypic.com/ejsv0k.jpg](http://i45.tinypic.com/ejsv0k.jpg)

how do i mount sda1 again?
sorry, i used to use ubuntu years ago, haven't touched it since and forgotten everything, just like my French :P
Boot into the Live USB. A hard drive should show up on the desktop as a filesystem. Double-click it and it should mount. If that doesn't work, then open a terminal (again, from the Live USB) and type:

sudo mount /dev/sda1 /mnt

That will mount the partition under the /mnt directory. You should be able to browse through it, pull files from it (which you should do in order to back them up immediately!), etc.

---

### Post by adjbck on 2012-09-16
> **jrog said:**
> Boot into the Live USB. A hard drive should show up on the desktop as a filesystem. Double-click it and it should mount. If that doesn't work, then open a terminal (again, from the Live USB) and type:

sudo mount /dev/sda1 /mnt

That will mount the partition under the /mnt directory. You should be able to browse through it, pull files from it (which you should do in order to back them up immediately!), etc.

Sir you are a genius, i could kiss you right now.
My mother sends her thanks. Now i have the documents how should i simply format the hard drive in gparted and install 12.04 ?

---

### Post by jrog on 2012-09-16
> **adjbck said:**
> Sir you are a genius, i could kiss you right now.
My mother sends her thanks. Now i have the documents how should i simply format the hard drive in gparted and install 12.04 ?
Excellent! Glad it worked out. :) I myself have done work on a dissertation, so I can't imagine how I'd feel if that work was potentially lost.

Assuming you have all of the data that you want stored elsewhere, you can now use the Live USB to install Ubuntu to the hard drive (there should be an icon on the desktop for this). If there's nothing else on the drive that you need, you can just tell it to use the whole hard drive and it will take care of everything else -- it'll wipe everything and reinstall.

HOWEVER, as I mentioned earlier, I have some suspicion that the hard drive may be dying, so it might be best not to rely on it for much until making sure that it is funtioning. There are ways of checking into that a bit more, if you're interested. Or you have the option of trying to reinstall, seeing if all functions well, and then waiting it out a bit to see if the hard drive holds up, I suppose.

EDIT: I just realized I may have misunderstood. You want to reinstall now as opposed to trying to recover the system that is on the drive, right? (I'd recommend entirely reinstalling, since the rest of the system isn't really essential to keep, as long as you have the documents you wanted.)

---

### Post by adjbck on 2012-09-16
> **jrog said:**
> Excellent! Glad it worked out. :) I myself have done work on a dissertation, so I can't imagine how I'd feel if that work was potentially lost.

Assuming you have all of the data that you want stored elsewhere, you can now use the Live USB to install Ubuntu to the hard drive (there should be an icon on the desktop for this). If there's nothing else on the drive that you need, you can just tell it to use the whole hard drive and it will take care of everything else -- it'll wipe everything and reinstall.

HOWEVER, as I mentioned earlier, I have some suspicion that the hard drive may be dying, so it might be best not to rely on it for much until making sure that it is funtioning. There are ways of checking into that a bit more, if you're interested. Or you have the option of trying to reinstall, seeing if all functions well, and then waiting it out a bit to see if the hard drive holds up, I suppose.

Id love to check up on it if you have the time to tell me, any chance to learn something new. Tbh i was thinking of getting her a MBA or something like that but it would still be nice to see how this thing is doing.

---

### Post by jrog on 2012-09-16
> **adjbck said:**
> Id love to check up on it if you have the time to tell me, any chance to learn something new. Tbh i was thinking of getting her a MBA or something like that but it would still be nice to see how this thing is doing.
Okay, you'll still need to be on the Live USB for this to work, and I think you'll need to be connected to the Internet, too. So, assuming you can do that, you should type the following at the terminal:

sudo apt-get update && sudo apt-get install smartmontools

Once that finishes, still at the terminal, you should type:

sudo smartctl -H /dev/sda

That will do a basic health check on the drive. It may tell you it's failing. If you want more detailed information, you can type:

sudo smartctl -a /dev/sda

If you're able, and interested in getting more info., go ahead and paste the output to a pastebin online. I'm interested in seeing the Load_Cycle_Count output by the last command, in particular.

---

### Post by drdos2006 on 2012-09-16
I see from your paste [http://paste.ubuntu.com/1209469/](http://paste.ubuntu.com/1209469/) that both sda and sdb hard drives are set to boot.
Boot up with a liveCD, run "gparted" and modify the flags and untick the "boot" flag on drive sdb.

Then reboot the computer.

regards

---

### Post by jrog on 2012-09-16
> **drdos2006 said:**
> I see from your paste [http://paste.ubuntu.com/1209469/](http://paste.ubuntu.com/1209469/) that both sda and sdb hard drives are set to boot.
Boot up with a liveCD, run "gparted" and modify the flags and untick the "boot" flag on drive sdb.

Then reboot the computer.

regards
sdb is his USB drive. It's set to boot so that he can use it as a Live USB. It won't conflict with sda when the USB isn't inserted.

---

### Post by jrog on 2012-09-16
OP, you should probably mark this thread as solved, by the way (using the "Thread Tools" at the top of the page). :)

Also, I'm going to be away from my computer for a bit, so I won't be able to be checking and quickly replying to this thread as I was (just FYI, so you don't wait for a response).

---

### Post by drdos2006 on 2012-09-16
OOps. I stand corrected.

regards

---

### Post by adjbck on 2012-09-16
> **jrog said:**
> Okay, you'll still need to be on the Live USB for this to work, and I think you'll need to be connected to the Internet, too. So, assuming you can do that, you should type the following at the terminal:

sudo apt-get update && sudo apt-get install smartmontools

Once that finishes, still at the terminal, you should type:

sudo smartctl -H /dev/sda

That will do a basic health check on the drive. It may tell you it's failing. If you want more detailed information, you can type:

sudo smartctl -a /dev/sda

If you're able, and interested in getting more info., go ahead and paste the output to a pastebin online. I'm interested in seeing the Load_Cycle_Count output by the last command, in particular.

I'll get round to this in the morning, thank you so very much with your help so far and if you don't mind I'll pm you with any questions that I have when I follow the quoted advice

---

### Post by jrog on 2012-09-16
> **adjbck said:**
> I'll get round to this in the morning, thank you so very much with your help so far and if you don't mind I'll pm you with any questions that I have when I follow the quoted advice
I don't mind at all; feel free!

---

