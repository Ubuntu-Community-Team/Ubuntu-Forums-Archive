---
title: "Label a Hardrive?"
date: 2009-02-17
forum: General Help
---

### Post by pickboy87 on 2009-02-17
Alright, so I was in the process of converting one of my other hard drives (not main) from NTFS to ext3. I used Gparted within Ubuntu and was able to successfully convert the drive to ext3. Now I've run into a problem. The label is simply coming up disk or the area that allows me to mount it "250.1 GB Media".

Is there someway to rename it? I've tried right clicking on the 250.1 GB Media in the Computer area of Ubuntu and trying to rename it that way. I get the following error:

Sorry, couldn't rename "250.1 GB Media" to "Downloads": Operation not supported by backend

The drive is unmounted by the way. Thanks for your help!

---

### Post by kanikilu on 2009-02-17
I believe you can set a label in gparted.

---

### Post by pickboy87 on 2009-02-17
> **kanikilu said:**
> I believe you can set a label in gparted.

I looked, I have a slightly outdated version though 3.5 vs 4.1 or whatever. There wasn't anything.

I did figure it out. I tried this earlier and it didn't work, so for whatever reason why it worked now...oh well.

```
sudo e2label <device> <label>
```

I simply changed the <device> to /dev/sdc and <label> to Downloads. It worked this time...

Thanks for the quick response. And yes, I did a bunch of googling and looking around before I posted :D

---

### Post by ghstridr on 2009-02-17
```
/sbin/e2label <device> [newlabel]

example: /sbin/e2label /dev/hda1 newdisk


```

I believe this is what needs to be done.
It also gives you the ability to mount partitions by label name in /etc/fstab instead of using that impossibly long and hard to remember UUID.

Note: You can't label the root device (ie. /dev/hda) it has to be a partition.  If you 3 partitions and you want to label just the last one:
```
e2label /dev/hda3 newlabel
```
You can also just specify the device name without a label and e2label will report back the label on the device if there is one.

---

### Post by Tootler on 2009-02-17
I was having a similar problem. I have my data stored on a fat32 partion so I could share it with Windows. I found that e2label doesn't work with fat partitions but I was able to rename from GParted. 

You need to unmount the partition, then select "Partion/Label" from the menu. This brings up a dialog box with the current label in. Delete the old label and type in your new one. "OK" it and then click on "Apply" in the toolbar and the partion will be renamed. 

Geoff

---

### Post by pickboy87 on 2009-02-17
Alright, I've run into a whole slew of new problems. So here goes:

My main drive is ext3 and running Ubuntu 8.04. No problems here, everything works just fine. I have 2 other HDD's that are also connected to my computer via SATA. One is 250gbs and the other is 500gbs. The 250gb one is the one I'm now tampering with. It was NTFS and was used as a backup/downloads drive. I decided to switch it over to a more native linux file system (ext3). Backed everything up, converted it to ext3 using the Gparted Live CD and was able to change the label that way.

I cannot seem to copy back the files to the drive. It acts like its read only. And whenever I right click to paste my files back in the drive, its greyed out as well as create folder. I'm kind of dumbfounded when it comes to file systems. Used to FAT/FAT32/NTFS. Which file system should I be using for that drive? I could always go back to NTFS, but I worry that it becomes defraggmented too easily and have no way of defragging in linux.

---

### Post by Zimmer on 2009-02-17
you need to alter the permissions on the drive.... spotted a post the other day about this and how to do it 'properly'.
I cheated on my backup drive by opening Nautilus as root and creating a folder on the drive, then altered the permissions of the folder to give user access....

this may work
[http://ubuntuforums.org/showthread.php?t=1070470&highlight=drive+permission](http://ubuntuforums.org/showthread.php?t=1070470&highlight=drive+permission)

This is better
[http://ubuntuforums.org/showthread.php?t=1060038&highlight=drive+permission](http://ubuntuforums.org/showthread.php?t=1060038&highlight=drive+permission)

---

### Post by pickboy87 on 2009-02-17
Awesome, that worked! I had to use the:

```
sudo chown -R nathan:nathan /media/Downloads
```

to get it to work properly. Thanks again :D It was set as root and wouldn't let me delete or modify anything on the drive.

---

### Post by Zimmer on 2009-02-17
[http://www.tuxfiles.org/linuxhelp/files.html](http://www.tuxfiles.org/linuxhelp/files.html)

A good read regarding Permissions..... I did read it a few years ago, and have forgotten the details, but remembered some of the principles (such as, do not lose the link to this page !!  :)  )

---

### Post by Psyphre on 2009-02-17
I dont know if this is of any help, but I remember once I booted into windows for some gaming. Then for some reason decided to change the name of one of my internal drives. When i logged back into ubuntu it recognised the new name and no longer used "250gb media"

---

