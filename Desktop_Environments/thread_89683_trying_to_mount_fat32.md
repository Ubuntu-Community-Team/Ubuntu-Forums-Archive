---
title: "trying to mount fat32"
date: 2005-11-13
forum: Desktop Environments
---

### Post by tomwell on 2005-11-13
Good morning to all...

Am trying to mount my fat 32 partition and when i type the command 

sudo mount -a i get this error message:

[COLOR="Red"]mount: wrong fs type, bad option, bad superblock on /dev/hda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/COLOR]

what do you guys think ?? I have mounted my windows partition in the same way and it works??? what could it be???

ps: what is the command to delete a dir in terminal....

Thx guys and have a tgreat sunday!!!

Tom

---

### Post by Ubuntist on 2005-11-13
What's the entry in /etc/fstab for /dev/hda5?

---

### Post by tomwell on 2005-11-13
the entry is 

[COLOR="Red"]/dev/hda5       /media/winfat32  vfat    iocharset=utf8,umask=000   0       0[/COLOR]

thx for looking into this man...!

---

### Post by Ubuntist on 2005-11-13
Well, for what it's worth, I too have a FAT32 partition that I access from Ubuntu.  At one stage I had iocharset=utf8, but that gave some error messages.  Now I have

[COLOR="Red"]
/dev/hdc7       /media/exc      vfat    umask=0000       0       0
[/COLOR]

and this seems to work just fine.

---

### Post by manicka on 2005-11-13
I use 

defaults,rw,umask=000 0 0

no problems

---

### Post by slux on 2005-11-13
I don't really see why vfat should be mounted with iocharset=utf8 since it's a filesystem that doesn't support utf8 AFAIK but I doubt that is what's causing you problems.

The most popular cause for the error you're experiencing is that the partition you're trying to mount simply does not contain the filesystem you're trying to mount it as. Double check that your windows partition is indeed /dev/hda5 and that you are using fat (as opposed to ntfs).

---

### Post by tomwell on 2005-11-13
this is my fdisk command...

[COLOR="Red"]Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         523     4200966   1b  Hidden W95 FAT32
/dev/hda2             524        7271    54203310    7  HPFS/NTFS
/dev/hda3            9216        9729     4128705    5  Extended
/dev/hda4   *        7272        9215    15615180   83  Linux
/dev/hda5            9304        9729     3421845    b  W95 FAT32
/dev/hda6            9216        9302      698764+  82  Linux swap / Solaris

Partition table entries are not in disk order
[/COLOR]

I am trying to mount the second fat 32 name hda5 since hda1 is my windows OS....

Its so weird....

---

### Post by fragmental on 2005-11-13
/dev/hdb4       /mnt/oldshare2     vfat    rw,uid=1000,gid=1000,exec,user            0 0

here's mine.  My user id and group id are 1000.  For multiple users, i could probably just set the gid to some group that they were all in and that would be ok.  Some of that line might be redundant, but i don't really care because it's working and I'd rather not fix something that's not broken.

---

### Post by slux on 2005-11-13
Are you using the stock ubuntu kernel? check that the vfat filesystem module is available and load it if it doesn't get loaded automatically.

Only other thing that could cause such problems that comes to mind is that you'd be having bad issues with the partition table not been written with the same geometry that ubuntu is seeing the disk with but that would probably create problems much worse than just not being able to mount a single vfat partition.

---

### Post by Irony on 2005-11-13
You might want to reformat the fat32 with Id 0C version of fat32;

[PHP]   Device Boot      Start         End      Blocks   Id  System
/dev/hda5           9304       9729    3421845    c  W95 FAT32 (LBA)
[/PHP]

You can do this in terminal with the *sudo cfdisk* command.

---

### Post by metoo on 2005-11-13
Can you mount it manually? In a console:
sudo mount -t vfat /dev/hda5 /media/winfat32 -rw

(/media/winfat32 does exist?)

If this works try the line:
/dev/hda5 /media/winfat32 vfat noauto,rw,users,noexec,umask=000 0 0

in your /etc/fstab (comment out '#' the existing one for /dev/hda5).

noauto = don't mount at boot (auto = mount at boot)

---

### Post by tomwell on 2005-11-13
metoo,

When i manually try to mount it gives me this error message:

[COLOR="Red"]mount: wrong fs type, bad option, bad superblock on /dev/hda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/COLOR]

Thank you very much...Am really grateful to all of you...!!!

Tom

---

### Post by tomwell on 2005-11-13
Irony,

I have tried the sudo cfdisk comand, and i get this error message:
[COLOR="Red"]
   FATAL ERROR: Bad logical partition 6: enlarged logical partitions overlap
                          Press any key to exit cfdisk[/COLOR]

I have a feeling all this problem has something to do with a previous post of mine that came to no avail where i was explaining that i had an extra partion...!!! 

[http://www.ubuntuforums.org/showthread.php?t=89260](http://www.ubuntuforums.org/showthread.php?t=89260) 

thats the post am talking about...

If anyone knwos anything Id really appreciate some help... am getting really worried...!!!

Thanks to all of you out there!!!

Peace 

Tom

---

### Post by slux on 2005-11-13
Your cfdisk error sounds like the kind of thing caused by disk geometry confusion. I wouldn't really worry about it too much although it's pretty strange and I'd really like to get a better understanding of why fdisk can be just fine with it but cfdisk complains. :P The values that fdisk is reporting for partition boundaries look pretty good in any case.

Have you created/formatted the fat32 partition or Windows or how did you go about creating it? you should try "modprobe vfat" before attempting the manual mount just to make sure, it does look like that's not the issue here but I'd like to remove the slightest possibility.

As I said on the other thread, having fdisk list  an extra partition is natural when having more than 4 partitions on a PC system so that's no cause for alarm.

---

### Post by tomwell on 2005-11-14
Slux thank you very much for helping me so, and taking the time to read my previous post, am going to delete evrything and install a new hard drive and then have one drive windows and the other bigger 120 GB drive linux... Am hooked on the possibilities of this great OS!!!!

The reason am keeping windows is just to play the great games unfortunately released on windows and since i do a lot of graphics i need to use my vector graphics Progs...

I'll keep ya updated on progress...

Once again thanks and thank you to all who helped...!!!

Peace 

Tom

---

### Post by tomwell on 2005-11-14
Ok Slux if ya interested,

I just went into windows and formated the fat 32 partition and Shazam!!!

No more mounting local files system failed!!!

And i have my fat 32 partition mounted on start up...

Dont know what that means except that i needed to format the drive in windows...

Hope that helps anyone in the same problem as me...

Peace to all!!!

Tom

---

