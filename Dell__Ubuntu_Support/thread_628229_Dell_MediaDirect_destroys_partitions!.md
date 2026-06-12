---
title: "Dell MediaDirect destroys partitions?!"
date: 2007-12-01
forum: Dell  Ubuntu Support
---

### Post by pseudomancer on 2007-12-01
I've found a few threads on this already, but nothing that answers the question conclusively.  A couple of hours ago I accidentally pressed the MediaDirect button on my laptop (Inspiron 640m), and when I tried to boot up the next time I got a GRUB "E 17" error and the system won't boot.  I tried using the Ubuntu 7.04 live cd to check things out, but it has me even more confused.  Something seems to be terribly wrong with my hard drive - I can't even mount my linux partition from the live cd.

Ideally I would like to get the system running again, but I can settle for figuring out how to mount my linux partition so that I don't lose my files.

gparted is (extremely) unhelpful: it claims /dev/sda is not partitioned (149.05 GiB unallocated or some such)

Output from `fdisk -l`:
```

Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       18746       19006     2096451    c  W95 FAT32 (LBA)
/dev/sda2               7        4087    32780632+   7  HPFS/NTFS
/dev/sda3            4088       19006   119836867+   f  W95 Ext'd (LBA)
/dev/sda4           19007       19457     3622657+  db  CP/M / CTOS / ...
/dev/sda5   ?       43857      118984   603455785   44  Unknown

```

Output from `mount -t ext3 /dev/sda5 /media/hd`:
```

mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Any suggestions?  Please help!

---

### Post by Skuzniak on 2007-12-01
Dell MediaDirect does have a habit of destroying partitions. There is only one way (that I know of) that will possibly allow you to save your data.

Press the MediaDirect button again to boot up. If you are incredibly lucky, it will revert the partitions back to the way they were. If not, you will have to hope that you can get lucky with mounting it.



To prevent MediaDirect from causing problems again, you will need to do a low-level format (a format that ignores the hard disk controller onboard the hard drive) to erase the hidden MediaDirect partition. The command to do this is the following:

HUGE WARNING!!! This will erase ALL DATA on your hard drive!! Be absolutely sure you want this before entering this command!!


dd if=/dev/zero of=/dev/sda

After entering that command, pressing the MediaDirect button to boot up will show a splashscreen, then cut to GRUB.

---

### Post by Dellfan on 2007-12-01
For a better understanding of how Media Direct works take a look at:

[http://www.goodells.net/dellrestore/mediadirect.htm]("http://www.goodells.net/dellrestore/mediadirect.htm")

If you boot form the LiveCd you may be able to repair/restore GRUB.

Media Direct is stashed on a hidden partition that normal drive commands don't even list. If you really want it gone you have to reformat the disk.

You can set it up dual boot using the Media Direct button is you want. Take a look at:

[http://forum.notebookreview.com/archive/index.php/t-180795.html]("http://forum.notebookreview.com/archive/index.php/t-180795.html")

---

### Post by pseudomancer on 2007-12-01
Unfortunately, pressing the MediaDirect button again doesn't fix anything.  And I would rather not zero my drive if I can avoid it.  I really need the data that was on there.

So if there's no way to store the hard drive to a sane state, can anyone tell me how to rescue a partition?  Is there some way to use dd_rescue or similar?

Thanks

---

### Post by atlas95 on 2007-12-02
I have try this allready :(
I had reinstall al y system, I only have ubuntu, I don't want a dual boot.
I'm afraid of pressing this key an other time.What is the solution?

---

### Post by Skuzniak on 2007-12-02
atlas95, if you want to prevent the MediaDirect button from causing problems again, you will need to zero your drive. This will delete ALL OF THE DATA on it. The command can be found in my previous post in this thread.

---

### Post by Nicolae on 2007-12-02
From the live CD, try installing and running testdisk. I used it before to recover my /home partition after the winxp installer decided to erase it. 

I honestly can't remember how to use it, but the wiki ( [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) ) was extremely helpful. It might allow you to recover your lost data, so you can nuke media  direct.

---

### Post by pseudomancer on 2007-12-03
testdisk worked amazingly well.  I couldn't fix my old install, but I saved all of my data.  Thanks!

---

### Post by nealron on 2007-12-28
**[SIZE="3"]I found a fix for the Dell Self-destruct-direct (MediaDirect) button problem.[/SIZE]** 

A little background info might be in order though. What the Dell MediaDirect button (next to the power button and has a house icon on it similar to an internet browsers "Home" button) does when the hard drive is partitioned in a way that it does not expect (aka, linux installed) it rewrites the partition table that it thinks it should have. Your partition table is essentially like the table of contents pages in a book with 100 billion pages, without it your screwed. 

What we're going to do here is offer a way to disable the button if you don't care about the data on the drive (like right after a fresh install) OR a way to recover your partition table with a nifty program called [testdisk]("http://www.cgsecurity.org/wiki/TestDisk").

**[SIZE="3"]Plan A - Disable Destruct Button[/SIZE]**
You can low-level format your hard drive to permanently remove the danger the button poses to your future data, because you _will_ loose ALL data currently on your drive. Issue the following command from a live CD/DVD booted system.

[B][SIZE="2"]****WARNING USE ONLY FROM LIVE CD/DVD******
****WARNING WILL DESTORY ALL DATA ON DISK*******[/SIZE][/B]
```
sudo dd if=/dev/zero of=/dev/sda
```

The above command writes zeros in every sector of your hard drive, aka "Zeroing the drive". Zeroing the drive has been known to overwrite the HPA (Host Protected Area) of the hard drive where the MediaDirect partition is hidden on the drive. Afterwards, pressing the self-destruct button will harmlessly show the MediaDirect splash screen and then boot GRUB.

[_The above came from Skuzniak here_]("http://ubuntuforums.org/showpost.php?p=3870754&postcount=2")

**[SIZE="3"]Plan B - RECOVER YOUR DATA[/SIZE]**.
If you have pressed the dreaded MediaDirect button and now have a very expensive paper weight for a laptop, FEAR NOT! testdisk to the rescue!

1) Boot up your live CD/DVD (like the one you used to install from).

2) Copy the additional repositories to your /etc/apt/sources.list file on your live CD/DVD session. The live CD isn't mean to install packages/programs to since it is erased when your reboot, however, if needed you can install a small amount of extra data. Like repair utilities. You can find instructions on how to do this [HERE]("http://kubuntuguide.org/Gutsy#Add_Extra_Kubuntu_Repositories").

3) Issue the following command to update your repository list after you changed your sources.list file and also install the precious data recovery utility "testdisk", as well as run testdisk after it's installed creating a testdisk.log file of all it's actions in the directory you issue the following command from.
```
sudo apt-get update && sudo apt-get install testdisk && sudo testdisk /log
```

4) Use the arrow keys to select your laptop hard drive. If you are using the live CD/DVD you should see two hard drives. 

**/dev/hda** (the live CD virtual drive) and **/dev/sda** (your laptop hard drive)

To "Proceed", tap the "Enter/Return" key when you've selected the appropriate hard drive.

5) Tap the "Enter/Return" key again on the next screen to select "Intel/PC" partition type.

6) Tap the "Enter/Return" key again on the next screen to "Analyse" (spelled the way it is in the program) your hard disk and search for your lost partitions.

7) This screen shows the screwed up partition table.. just tap the "Enter/Return" key again to "Proceed"

8) If you're lucky you'll see two or three partitions (If you let Ubuntu install configure your disk for you). Something like what you see below:
```
* Linux 0 1 1 18752 254 63 301266882
L Linux Swap 18753 0 1 19456 254 63 11309760
```
Tap the "Enter/Return" key again to "Proceed"

9) Now tap the right arrow key twice and tap the "Enter/Return" key to write the recovered partition table. Confirm it by taping the "Y" key and then the "Enter/Return" key.

10) Reboot your computer and take the live CD/DVD out. :)

NOTE: I had to do this twice for it to work for some reason, but after that, my precious Kubuntu booted up normal just like it used to without one file missing!

THANK YOU [_NICOLAE_]("http://ubuntuforums.org/showpost.php?p=3878125&postcount=7") and [_PSEUDOMANCER_]("http://ubuntuforums.org/showpost.php?p=3885747&postcount=8")!

---

### Post by mike999999 on 2008-01-12
Heres something to try before going through all this reformat - format hassle. 

So you've pressed the media direct button and get grub 17?

Turn it off and press it again. 

Oh, it still doesn't boot?

Turn it off and press it again. 

Voila! Working system. 

Tested and verified. :guitar:

---

### Post by rhonaldmoses on 2008-02-02
Hi, I am following your post, but I see no messages on the screen after I issue the command (neither the control does not return to the prompt)... how long should I wait for this process to complete (zero-ing the sectors).

---

### Post by davide.del.vento on 2008-04-28
> **Skuzniak said:**
> 

HUGE WARNING!!! This will erase ALL DATA on your hard drive!! Be absolutely sure you want this before entering this command!!

dd if=/dev/zero of=/dev/sda

After entering that command, pressing the MediaDirect button to boot up will show a splashscreen, then cut to GRUB.

That's great, it is able to destroy the evil MediaDirect (and everything else, 'course). Maybe using a bs=1024 it should be faster...

Now the button is safe.

For the record, I've been told that some Dells have a setting in the BIOS by which you can disable that button (there isn't in mine). You may want to check, before starting such a grind.

Thanks a lot.
;Dav

---

### Post by mailforbiz on 2008-04-30
This is what I use.

```
sudo dd if=/dev/zero of=/dev/sda bs=1024& pid=$!
```

If you want to check the status of the zeroing, use

```
sudo kill -USR1 $pid
```

This basically sends a USR1 (INFO) signal to the process and forces it to print out statistics and resume (don't worry, it doesn't kill the process). 

Cheers.

---

### Post by Saberu on 2008-05-02
I registered especially to reply to this thread because I think it's unfair that no one has offered a simple solution to this problem.

Having just accidentally pressed this evil button after checking what the button did to screw the booting up and a few minutes of thinking I realised I could fix it by resetting the MBR to the windows partition. 

I did that using an MBR tool and it took me all of 2 seconds. So here is a good alternative solution if you don't feel like going through all the hassle of reinstalling just to disable the button.

I think the tool I used was called Magic Boot, very intuitive.

You guys just got owned by a Windows user :lolflag:

---

### Post by MuddyAzian on 2008-07-20
I have a XPS M1330 that is dual booted with Windows XP and RHEL 5.1.  I accidentally pressed the stupid Dell Media Direct home button when the laptop was powered off, and ruined my partition and GRUB install.  When I tried the reboot, I got a blank black screen with "GRUB" showing, and that's it.  Okay, I don't use ubuntu, but I thought I'd reply in case there are any RHEL (or possibly Fedora) users out there that will run into the same problem (and perhaps what I did will carry over to ubuntu).  This is what I did to fix it:

Booted with KNOPPIX 5.1.1, and ran testdisk.  The MEDIADIRECT partition and the Linux partition were trying to occupy the same space, and I was getting conflict errors in testdisk.  So I made the Linux boot partition the primary boot partition, instead of the MEDIADIRECT partition.  That didn't really fix it, but it *MIGHT* be necessary as a prerequisite for the following secondary fix:

Then, I reinstalled GRUB using the RHEL 5.1.1 installation disk using the linux rescue option.  Details can be found here: [http://www.redhat.com/docs/manuals/enterprise/RHEL-5-manual/en-US/RHEL510/Installation_Guide/s2-rescuemode-boot-reinstall-bootloader.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-5-manual/en-US/RHEL510/Installation_Guide/s2-rescuemode-boot-reinstall-bootloader.html) After reinstalling GRUB and rebooting, everything magically worked fine!

This fix *might* work for Fedora, as well, but I did not try.  Good luck!

:guitar:

---

