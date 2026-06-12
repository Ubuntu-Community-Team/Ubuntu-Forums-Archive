---
title: "Specify existing home folder on seperate hard drive as home?"
date: 2009-02-27
forum: General Help
---

### Post by Dr.Suave on 2009-02-27
Hiya

I recently managed to mess up an Ubuntu 8.10 installation with my needless tinkering, and as I'm only using the hard drive for another couple of days I thought I'd just make a new partition and install 8.10 on there.

Anyway, my home folder on the original partition is still intact - is there any way I can tell ubuntu to use that one instead of the newly made home folder?

I've heard about people setting their home folder to separate partitions before, but is there a way to set your home folder to an existing home folder on a separate partition?

Thanks a lot, I hope I worded the above clearly - I'm not feeling very articulate today!

---

### Post by geirha on 2009-02-27
Sure is. Where is the second partition currently mounted? I'll assume [COLOR="Blue"]/media/sda1[/COLOR], but change it to the correct one in the following instructions

The following instructions also assume that your username in the other install is the same as in the new install, and that the users in each system has the same uid.
Check this by opening a terminal and running
```
ls -ld $HOME [COLOR="Blue"]/media/sda1/[/COLOR]$HOME
```
They should both output the same owner; third and fourth field. If that is not the case, do NOT proceed with the following.

Hit alt+F2 to get the run dialog and type "gksu gedit /etc/fstab"
In the /etc/fstab file, add the following line (at the end of the file):
```
[COLOR="Blue"]/media/sda1[/COLOR]/home /home none bind 0 0
```
Reboot, and /home should now be your old /home.

---

### Post by thtrgremlin on 2009-02-27
If this is the way you want to do it, it is simple, but it involves some delicate configuration / tinkering, but that sounds like your thing.

1. login to recovery mode.

2. backup and remove the contents of your old home directory

3. add the old hard drive to your /etc/fstab to your media folder. There may be some extra failsafe options you need to add in case anything goes wrong, but this should still work as is.

4. create a symbolic link in your root directory called home that links to the home directory on the old drive
[COLOR="Red"]
note / edit: geira's suggestion is better. That is a much better way of linking.[/COLOR]

However, personally, if it is just your home directory that is screwed up, I would say backup what you want to keep, then from recovery mode delete the user account and make a new one. viola, fresh, correctly configured user. Another method I have used is to create a new user and copy their config files to replace specifically screwed up files.

Also, 'chroot' is an awesome tool to learn to use along with a LiveCD. 

Sorry to be vague, but if you don't know how to do those steps on your own, it would be a bit much for me to walk you through the whole thing, but I hope you can work something out with a small amount of research with the above suggestions.

Best Luck!

---

### Post by Dr.Suave on 2009-02-27
Thanks!

The values are the same, but the second partition is mounted as media/disk - does this matter? Should I change the mount point to an sda number before continuing?

Thanks again
Wilf

---

### Post by Dr.Suave on 2009-02-27
thtrgremlin - intriguing! But unfortunately I'm in a pretty tired state right now, and will probably mess that one up :)

---

### Post by thtrgremlin on 2009-02-27
> [COLOR="Red"]add[/COLOR] the following line (at the end of the file)

You do not need to get rid of the old entry. just add the new one. It just means there will be multiple ways to get to stuff.

---

### Post by thtrgremlin on 2009-02-27
> **Dr.Suave said:**
> thtrgremlin - intriguing! But unfortunately I'm in a pretty tired state right now, and will probably mess that one up :)

As much as it might be fun to tinker, geirha really has the right way of doing it.

Best luck!

---

### Post by geirha on 2009-02-27
> **Dr.Suave said:**
> 
The values are the same, but the second partition is mounted as media/disk - does this matter? Should I change the mount point to an sda number before continuing?


Last time I installed ubuntu next to another ubuntu install, it set up mounting of the other ubuntu partitions by their device name. E.g. /dev/sda1 got mounted to /media/sda1, /dev/sda2 to /media/sda2 etc. Things has probably changed since then, but it does not matter what directory it is mounted at, just make sure you change /media/sda1 with /media/disk in my instructions.

There must be an entry in /etc/fstab for the other partition though. I forgot to take that into consideration in my last post. Do you see any output from this command? ```
grep '^.\+/media/disk' /etc/fstab
``` If so, that's good :)

The reason this is important is that there are two ways to mount a partition. One is having an entry in /etc/fstab, and another is by mounting it with nautilus in gnome. If the latter is the case, you'll also need to add an entry for your second partition in /etc/fstab.

---

### Post by Dr.Suave on 2009-02-27
No, I'm afraid that command doesn't bring anything up for me - I was mounting the drive in nautilus beforehand, but I've now configured and renamed it in fstab with
```
/dev/sda3 /media/old ext2 rw,suid,dev,exec,auto,user,async
```
I can't seem to get your fstab entry to work - here's a copy of my fstab file, just in case the mistake I've made somewhere is obvious -
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=ee03727d-71bc-4f6e-aa6f-5bfb55f83aa9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=169267b0-b2e2-4cd9-a8f2-3f7995fd4a47 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# note! the following is a re-allocation of home, and some mount options for the old partition:
/media/old/home/ /home none bind 0 0
/dev/sda3       /media/old     ext2    rw,suid,dev,exec,auto,user,async        0       2  
#/dev/sda3 /home/home ext2 nodev,nosuid 0 2
```
Having the drive automounted is close enough to what I need, so we don't need to lose any sleep if specifying a new home is more complicated then it looked.

Thanks for all the help, guys
Wilf

---

### Post by geirha on 2009-02-27
This line is correct
```
/media/old/home/ /home none bind 0 0
```
but /media/old must've already been mounted, so it needs to appear after the line that mounts /dev/sda3 to /media/old (The filesystems are mounted in the order they appear in /etc/fstab)

Also, I'd change the sda3 line to read:
```

/dev/sda3       /media/old     ext3    defaults        0       2  

```
It most likely has ext3 filesystem, unless you specifically set it to ext2. (An ext3 filesystem is an ext2 filesystem with some extra features, and can be mounted as ext2, but then journaling won't be used). And the defaults option is the same as rw,suid,dev,exec,auto,nouser, so it makes it a bit shorter, and the user option is not needed since it will be mounted by root.

Another thing I'd do is to change /dev/sda3 with its UUID like your / and swap partition has. To find the UUID of /dev/sda3, you run the command ```
sudo blkid /dev/sda3
```

Lastly, the directory you specify as mount point in /etc/fstab must exist beforehand (unlike when mounting it from nautilus), so make sure it's created ```
sudo mkdir -v /media/old
```

---

### Post by Dr.Suave on 2009-02-27
Actually, for some reason that partition is formatted as ext2 - I have no idea what compelled me to do that. :)

Anyway, the reshuffling of lines worked! Thanks for the help! Much appreciated!:KS

---

### Post by geirha on 2009-02-27
Well, I used ext2 for many years, and didn't have much trouble with it, but ext3 does have more advantages.[quote=Wikipedia]Its main advantage over ext2 is journaling which improves reliability and eliminates the need to check the file system after an unclean shutdown.[/quote]

It's easy to convert to ext3. Boot the ubuntu CD (to ensure it is not mounted) and run ```
sudo tune2fs -j /dev/sda3
``` and of course make the appropriate change in fstab.

Anyway, glad to hear you got it sorted :)

---

### Post by thtrgremlin on 2009-02-28
Just curious geirha, what are the advantages of using the UUID? Is it so that fstab isn't dependent on grub mappings in case these is some kind of update? Just always wondered.

---

### Post by geirha on 2009-02-28
Saves you the trouble when shuffling harddrives. UUID are always the same, while the device names sda, sdb, sdc etc. are not necessarily. [https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

---

### Post by thtrgremlin on 2009-02-28
Thanks! I know a few people to pass that info onto. I've had my system in the past not boot because of this (in hindsight).

---

