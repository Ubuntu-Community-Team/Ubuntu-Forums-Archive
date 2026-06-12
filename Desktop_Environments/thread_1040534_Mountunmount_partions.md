---
title: "Mount/unmount partions"
date: 2009-01-15
forum: Desktop Environments
---

### Post by Neptune070 on 2009-01-15
HI everyone.
I am new to ubuntu and i absolutely love it... although i came across may issue this forum had answers to almost all my predicament.
I have a dual boot with ubuntu and xp and they seem to be working fine.
I have the following partions
/dev/sda1  NTFS   /windows (windows is installed here)
/dev/sda5  EXT3   /         (ubuntu is installed here)
/dev/sda6  linux-swap
/dev/sda7   NTFS            (this partion is not mounted)

here what i would like to do?
i dont want the /dev/sda1 to mount at all on start up - infact i dont want ubuntu to use that partion at all or have access to it
I want /dev/sda7 to show up as my /windows partion and be automatically mounted while boot

hope this would be possible...
thanks in advance....

---

### Post by ajgreeny on 2009-01-15
You could either edit the** /etc/fstab** file manually or search in synaptic for "ntfs" and install **ntfs-3g** (if it's not already there) and **ntfs-config** which lets you change the automounting of any ntfs partitions on your box.

If you're new to ubuntu I recommend the second way, though it could be worth your while looking into the fstab contents before and after to see what has been added and then search out what it all means.  Here's a good site:-
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by Neptune070 on 2009-01-15
i was digging around for options in the forum and got bits of info here and there and tried out those commands...

i did gksudo gedit /etc/fstab
out put:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=edba228e-3536-41d9-be0e-dbf406c832e8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=795d8157-8729-47a6-83f1-b3de9dcef9dc /home           ext3    relatime        0       2
# /dev/sda1
UUID=A2F80C3AF80C0F6B /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=3b8a64aa-a566-46ff-bdb2-bbc94fa1374e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

pls sugest what changes i should do to this file

my UUID for the partion i want to load permanently is F220ADBD20AD8965

pls suggest the correct command that i should append to add this file to mount while i boot with complete access

---

### Post by ajgreeny on 2009-01-15
Are you sure about your original list of partitions as your fstab file shows sda1, sda5, sda6 and sda8.  Let's see the output of ```
cat /etc/fstab
``` to be sure what we are dealing with.  You also appear to have a separate /home partition, a great idea, but it is necessary to be sure about what other partitions are present.

---

### Post by Neptune070 on 2009-01-15
Thanks for replying so fast
heres what i got
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=edba228e-3536-41d9-be0e-dbf406c832e8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=795d8157-8729-47a6-83f1-b3de9dcef9dc /home           ext3    relatime        0       2
# /dev/sda1
UUID=A2F80C3AF80C0F6B none        ntfs    defaults,umask=007,gid=46 0       0
# /dev/sda6
UUID=3b8a64aa-a566-46ff-bdb2-bbc94fa1374e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
jeeson@jeeson-desktop:~$ 

I changed UUID=A2F80C3AF80C0F6B to none and pass to 0 and now it does not mount that drive... i was wondering to delete the whole bit about #/dev/sda1 from the fstab so that that drive would not be used at all

and then typing in this command to use my other partition instead
# /dev/sda7
UUID=F220ADBD20AD8965 /media/Windows ntfs      defaults,dmask=027,fmask=137   0 1

i still cannot figure out what this --> dmask=027,fmask=137.... does?
i am only using it because it say so there... 
i would want to access and rewrite all the files in this drive - have complete access to it from ubuntu as well as from win xp - my dual boot..

thanks you for helping

---

### Post by s|fr on 2009-01-15
If from what you are saying is correct and there exists a /dev/sda7. then:

in you /etc/fstab

change

<code>
# /dev/sda1
UUID=A2F80C3AF80C0F6B /windows ntfs defaults,umask=007,gid=46 0 1
</code>

to

<code>
# /dev/sda7
/dev/sda7 /windows ntfs defaults 0 1
</code>

Do make sure to back up your old fstab before you do this. Hopefully this will work if not you can always revert from the backup.

---

### Post by Neptune070 on 2009-01-15
so are you saying that i do not need "dmask=027,fmask=137" after default
and that i dont need to use UUID

---

### Post by ajgreeny on 2009-01-16
Just to be certain, let us see the output from ```
sudo fdisk -l
``` which will be the best way to be sure of your disk partitions and make sure we get the fstab right.

---

### Post by FIONEX on 2009-01-16
I suggest using UUID's instead of /dev/sda1 .  UUIDs stay the same but device blocks (/dev/sda1) can change if you create/delete partitions.  That's why ubuntu stopped using device blocks and started using UUIDs in fstab.  Now, I guess it doesn't really matter as long as you don't create or delete partitions.

If you want to stop a partition from mounting, just put # in front of its mount line. Like this:
```

# THIS LINE DOESN'T MEAN ANYTHING BECAUSE IT'S COMMENTED OUT WITH A "#"!
# UUID=A2F80C3AF80C0F6B /windows ntfs defaults,umask=007,gid=46 0 1

```
Changing the UUID to 0 just confused the mounting program and that's why it stopped mounting the windows partition (which was your intended outcome anyways LOL).  I suggest commenting out the line instead...

fmask and dmask are just "umask" but for files (fmask) and directories (dmask).  A umask sets the permissions to any file/directory without permissions.  So if your umask is 007, then each directory has a mod of 770.  You calculate it like this: (mod = 777 - umask).  Therefore, you don't really need to set fmask and dmask since security isn't of the utmost importance.

Permissions of 775 are as follows:
the first 7 = read, write and execute for the owner of the file
the second 7 = read, write, execute for the group that the owner belongs to
the last digit 0 = no access for all other users that aren't part of the owner's group.


Go through this code to see what i did.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda5
UUID=edba228e-3536-41d9-be0e-dbf406c832e8 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda8
UUID=795d8157-8729-47a6-83f1-b3de9dcef9dc /home ext3 relatime 0 2
# /dev/sda1
[COLOR="RoyalBlue"]# COMMENT OUT THE NEXT LINE LIKE THIS:
#UUID=A2F80C3AF80C0F6B none ntfs defaults,umask=007,gid=46 0 0[/COLOR]
# /dev/sda6
UUID=3b8a64aa-a566-46ff-bdb2-bbc94fa1374e none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

# ADD something like this
[COLOR="Red"]# Make sure that the directory you created is capitalized also: /media/Windows[/COLOR]
# /dev/sda7
UUID=F220ADBD20AD8965 /media/[COLOR="Red"]Windows[/COLOR] ntfs defaults,umask=007,gid=46 0 0

```

I also noticed that you like to use capitals in your directories and files.  It's really not recommended for linux because it gets hard to remember what's capitalized and what's not.  So just set a convention for yourself and always stick to it, or just don't capitalize at all.

---

