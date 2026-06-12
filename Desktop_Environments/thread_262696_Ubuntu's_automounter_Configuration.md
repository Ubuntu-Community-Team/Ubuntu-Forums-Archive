---
title: "Ubuntu's automounter: Configuration"
date: 2006-09-22
forum: Desktop Environments
---

### Post by mssever on 2006-09-22
I've noticed many questions here about permissions and other problems on removable Windows-formatted disks. Fixing the permissions is simple in fstab; the problem is that removable devices have changing names. If they were ext3 partitions, they could be mounted using a LABEL= device, but that doesn't apply to vfat/ntfs AFAIK. All that means that the ideal solution would bypass fstab for removable media--while still allowing configuration of mount options.[LIST=1]
[*]What program does Ubuntu use to auto mount?
[*]I know that pmount is involved in the process, but the pmount man page doesn't give any info about how to customize mount options. For example, I think that Win filesystems should be mounted with umask=000. How do I set that up?
[*]How do I make the automounter use ntfs-3g instead of ntfs?
[*]Is there any documentation on this somewhere? I couldn't find anything useful through Google.[/LIST]

---

### Post by RAOF on 2006-09-22
I can't give you an actual solution, but **gnome-volume-manager** is the daemon that actually notices that a new removable thingamabob has been added, and calls pmount.  You might want to search for configuration there.

---

### Post by mssever on 2006-09-22
Thanks for the tip. gnome-volume-manager ought to come in handy for something. Unfortunately, it's a Gnome program, and I have yet to see a gnome program with adequate documentation. And Google didn't turn anything up, either.

I did find out that hald is what notices a new drive, and udev is involved in the process--before gnome-volume-manager, I believe. I'm guessing that gnome-volume-manager calls pmount. But I still haven't discovered where to configure mounting.

man pmount lists the mount options that pmount uses: async,atime,nodev,noexec,noauto,nosuid,user,rw. The necessary options are listed in the manpage, but I don't know how to configure how it's called.

---

### Post by mssever on 2006-09-22
Anybody able to help?

---

### Post by skymt on 2006-09-22
gnome-volume-manager configuration is done through GConf (desktop > gnome > volume_manager). I looked through it, and there doesn't be anything relevant to your problem. Sorry. :(

---

### Post by etola on 2006-09-24
> **mssever said:**
> [LIST=1]
[*]What program does Ubuntu use to auto mount?
[*]I know that pmount is involved in the process, but the pmount man page doesn't give any info about how to customize mount options. For example, I think that Win filesystems should be mounted with umask=000. How do I set that up?
[*]How do I make the automounter use ntfs-3g instead of ntfs?
[*]Is there any documentation on this somewhere? I couldn't find anything useful through Google.[/LIST]

Hi, 

I had a similar problem and googled out some answers. What you need is to create a rule file for udev. When you plug your external disk, udev creates mount points for it something like sd*. Instead of this, you need to create a new mount point and tell udev run a script you prepared when this device is plugged-in. 

To do this: 
1. Plug your device and mount it usually. Then call 
 udevinfo -a -p /sys/block/sda --> you have insert your devices sd* here.  You are doing this to get some information about your drive to identify it in a rule file.

2. put your rules file under /etc/udev/rules.d/ with a name like 10-local.rules

3. your rule file should be like 

KERNEL=="sd*",SYSFS{size}=="308206223",SYMLINK+="mydisk",RUN="your_script"

this will create a symbolic link for your device and run your script to mount it. since you named it as mydisk* and not some random sdb5 or stuff, your script will be able to correctly identify it.

---

### Post by mssever on 2006-09-25
Thanks. This works for a specific device--which is better than nothing, and which I will use temporarily--but I was looking for something that would affect EVERY removable device.

I decided to hunt through the gnome-volume-manager source code to find out where the mount options get set. Beginning on line 1400 of src/manager.c, there are a number of mount options--presumably constants. But I'm not a C programmer, and I can't find where those constants (or variables?) get set. I've searched through every file in the source disribution and I can't find a single occurance of the string "MOUNT_UMASK" aside from the section I mentioned. MOUNT_UMASK has to be defined somewhere, but where? Anyone able to find that?

---

### Post by gilgongo on 2006-09-25
Personally, I think auto-mounting is one of the biggest problems that Ubuntu has. If I buy, say, a USB SD card reader and plug it in to my machine, Ubuntu either simply doesn't see it, or sees it but mounts it as root. The latter is related to the second biggest problem IMO, which is only letting root access certain devices. For example, I have to start Kino as root in order for me to grab video. That's not right at all.

Sorry, I know that wasn't a constructive comment - just venting...

---

### Post by mssever on 2006-09-25
> **gilgongo said:**
> Personally, I think auto-mounting is one of the biggest problems that Ubuntu has. If I buy, say, a USB SD card reader and plug it in to my machine, Ubuntu either simply doesn't see it, or sees it but mounts it as root. The latter is related to the second biggest problem IMO, which is only letting root access certain devices. For example, I have to start Kino as root in order for me to grab video. That's not right at all.

Sorry, I know that wasn't a constructive comment - just venting...

The problem of mounting as root is exactly the problem I'm attempting to fix. I will definitely post the solution here when I find it. I'm hoping someone will come along with at least a little information to help.

---

### Post by Yellow Onion on 2006-09-26
it uses pmount's default settings which are in the the program so its impossible to change without recompiling (line 24 in the fs.c file)
ill try to recompile it c wat happens (im a n00b so this mite take a while :P)

---

