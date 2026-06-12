---
title: "Making a read-only live USB"
date: 2016-07-30
forum: Desktop Environments
---

### Post by tychus2 on 2016-07-30
I’m trying to create a custom live USB that, by default, only mounts all media as read only (internal hard drives and USB sticks included) so that I don’t change files unintentionally. The detail is a bit long but please bear with me. 

Ideally I would like:

·       All media (including internal HDDs and USB drives) to NOT be automatically mounted
·       In Nautilus (file explorer), they would be detected and shown in the left column, which is the current action, but still not mounted.
·       Clicking on the drive in Nautilus would mount the drive as read-only, as opposed to the current action which is to mount with read/write privileges.
·       The only drives which are exceptions to this would be the live USB mounted drives, where changes aren’t stored on the USB but in actuality temporarily in memory, and are lost on shut down. I am not intending to use persistence.

Nautilus screenshot below for reference.
[ATTACH=CONFIG]270457[/ATTACH]
 
So far, my NTFS hard drive doesn’t mount by default which is good. I have also managed to disable automount for USBs by typing the following in the terminal:
gsettings set org.gnome.desktop.media-handling automount false
 
However, clicking in Nautilus on the hard drive/media shortcut on the left column mounts a volume with read/write privileges. Ideally, I want this mounting-on-click to be read-only, but if this is not possible, I would settle for having the drives auto-mount as read-only on detection (and therefore before clicking).
My investigations has so far shown up that I can use udiskctl to mount partitions read only from the terminal. Using this command, the shortcut to the mount point appears on the left column in Nautilus and the files are mounted under /media/Ubuntu/VOLUME_LABEL. The ‘VOLUME_LABEL’ folder is created and deleted on mount and unmount respectively, which is all perfectly how I want it!

For example, I can mount read-only by typing:

```
udiskctl mount –o ro –b /dev/sdc1
```

Next, I’ve been trying to use udevadm and to run this command on and partitions as soon as detected. To do this, I made a rule file in /etc/udev/rules.d/80-custom.rules with the following text:

```
KERNEL==”sd??”, RUN+=”/usr/bin/udiskctl mount –o ro –b /dev/%k”
```

I then enabled the new rule and tested it:

```

Udevadm control –reload
Udevadm test /block/sdc/sdc1

```

The test output stated that the RUN command is used.

> run: ‘/usr/bin/udiskctl mount –o ro –b /dev/sdc1’

So it appeared to work when I use the test function but when I actually insert a USB, it doesn’t mount automatically with this new rule, even though all the sources I’ve read seem to imply that it should.

So my first question is, how do I get the rule to work? Secondly, I’d like to know if anyone has managed to do what I’m trying here already and can help me figure out how to make all media read-only by default.

I am using Ubuntu 16.04.1, 64 bit. 

I’d appreciate any help you can give. Thanks for your time.

---

### Post by frostschutz on 2016-07-30
consider mount -o loop,ro instead of just ro, which is not readonly at all for some filesystems.

another option might be blockdev --setro / -getro to make block devices readonly on their own, but this can be difficult to maintain through all layers (partitions, device mappings, ...).

to my knowledge there is no existing live linux that strictly enforces readonlyness. even systems meant for rescueing things (systemrescuecd et al) mount stuff readwrite and start up RAIDs unasked.

I'm not too familiar with udiskctl but sometimes when stuff is run from a cron job or udev rule, environment variables are missing or it might just refuse to run as root. for starters make it write stdout/stderr/exitcode to a file so you can check for errors, if that fails you can run it through strace.

---

### Post by tychus2 on 2016-08-02
Thanks frostchutz, I’ve managed to progress a bit. First I’ll respond on your points specifically then I’ll explain where I’m at overall in a separate post.

> consider mount -o loop,ro instead of just ro, which is not readonly at all for some filesystems. 

Did you mean mount –o noload,ro instead of –o loop,ro?

It makes sense to me if you meant ‘noload’ as I looked through ‘man mount’ and it explained about read-only not being truly read-only in some cases. If you did still mean ‘loop’, then would you be able to explain what it does because I thought that that was used for mounting pseudo-devices like DVD ISO files.

>  another option might be blockdev --setro / -getro to make block devices readonly on their own, but this can be difficult to maintain through all layers (partitions, device mappings, ...). 

I am using this in my code now. It does indeed make the partitions read-only but there are some mounting issues now which I will discuss in the next post.

>  to my knowledge there is no existing live linux that strictly enforces readonlyness. even systems meant for rescueing things (systemrescuecd et al) mount stuff readwrite and start up RAIDs unasked. 

Some distros for forensic purporses do include read-only as a standard feature:
[URL="http://www.caine-live.net/"]
http://www.caine-live.net/[/URL]

>  The important news is CAINE 7.0 blocks all the block devices (e.g. /dev/sda), in Read-Only mode. You can use a tool with a GUI named BlockON/OFF present on Caine's Desktop.
This new write-blocking method assures all disks are really preserved from accidentally writing operations, because they are locked in Read-Only mode.
If you need to write a disk, you can unlock it with BlockOn/Off or using "Mounter" changing the policy in writable mode. 

>  I'm not too familiar with udiskctl but sometimes when stuff is run from a cron job or udev rule, environment variables are missing or it might just refuse to run as root. for starters make it write stdout/stderr/exitcode to a file so you can check for errors, if that fails you can run it through strace. 
I’m not too experienced with stdout/err/exitcode and strace but I gave them a go. With stdout/stderr I tried getting the RUN command to output to file.

```
 RUN+="/usr/bin/udisksctl mount -o ro -b /dev/%k >> ~/output.txt 2>&1” 
```

However, no file is created. I also tried using strace on upstart-dev-bridge but couldn’t find anything. I couldn’t understand all of the output but I was also unable to find anything matching the search terms ‘mount’ or ‘sdc1’,etc. Probably I’m not using them correctly though and would value your input as someone more experienced on how to do this properly

---

### Post by tychus2 on 2016-08-02
[SIZE=2]To summarise where I’m currently at:

I am trying to make a live USB that, by default treats all media, including internal drives and USB sticks) as read-only. I have managed to make the partitions read only using a udev rule and blockdev (Code will be shown later). [/SIZE]Now I am trying to deal with issues around mounting the read-only partitions.[SIZE=2]

Nautilus, by default, lists partitions along the left column. Clicking on a partition should mount it (if it isn’t auto-mounted) and ideally I’d like this action kept intact for read-only mounts. With the blockdev rule set, my FAT32/FAT volumes mount successfully and are read-only due to blockdev. The NTFS partitions, however, fail to mount. Testing ‘mount’ manually from the terminal, I found that the NTFS partition would only mount successfully if the read-only option is stated explicitly in the mount command (i.e. mount –o ro /dev/sdc1 /media/somefolder’), likely due to the partition itself now being read-only, and which Nautilus doesn't do when I click-to-mount.

To get around the Nautilus mounting problem, I have decided to try to auto-mount the volumes by modifying my custom rules. Previously, I had disabled automount in gsettings (see previous posts) which would not work with my NTFS partitions anyway for the reason stated in the last paragraph. 
I have created the file ‘/etc/udev/rules.d/99-custom-media.rules’ and inserted the following text:

```

# Make both the disks (e.g. sda) and partitions (e.g. sda2) read-only.
KERNEL=="sd*", RUN+="/sbin/blockdev --setro /dev/%k"
 
# Skip code if not matching expected kernel name for a partition
KERNEL!="sd[a-z][0-9]", GOTO="custom_media_rules_end"
 
# Import FS info
IMPORT{program}="/sbin/blkid -o udev -p %N"
 
# Get a label if present, otherwise specify one (used for mounting folder).
ENV{ID_FS_LABEL}!="", ENV{dir_name}="%E{ID_FS_LABEL}"
ENV{ID_FS_LABEL}=="", ENV{dir_name}="%k"
 
# Mount and unmount actions.
ACTION=="add", RUN+="/bin/mkdir -p /media/%E{dir_name}", RUN+="/bin/mount -o ro /dev/%k /media/%E{d$
ACTION=="remove", ENV{dir_name}!="", RUN+="/bin/umount -l /media/%E{dir_name}", RUN+="/bin/rmdir /m$

LABEL="custom_media_rules_end"

```[/SIZE][SIZE=2]
 
[/SIZE]Note that I was originally trying to use udisksctl instead of mount, as described in my original post, due to the fact that it automatically generated and removed the mount folder, but I couldn't get it work at all, whereas 'mount' is partially working currently. As such, part of the code above is to do with generating an appropriate folder name and creating and destroying it for mounting and unmounting respectively.
[SIZE=2]
I then reloaded the rules (udevadm control –reload-rules) and inserted my USB drives to see if it worked, which is where I’m currently having issues now.
My FAT32 and FAT partitions are auto-mounting successfully, but my NTFS partitions are coming up with the following error dialog box

[/SIZE][ATTACH=CONFIG]270538[/ATTACH][SIZE=2]

I have found that lots of people have been having problems auto-mounting with udev and specifically the ‘Transport endpoint is not connected’ error but none of the solutions I have tried have worked or are suitable. If anyone can help here, I’d value your input. I've included some quotes from other sources that may shine a light on the issues and a solution.


From [/SIZE][https://wiki.archlinux.org/index.php/Udev#Udisks](https://wiki.archlinux.org/index.php/Udev#Udisks):[SIZE=2] 
>  Warning: To mount removable drives, do not call mount from udev rules. In case of FUSE filesystems, you will get Transport endpoint not connected errors. Instead, you could use[udisks]("https://wiki.archlinux.org/index.php/Udisks") that handles automount correctly or to make mount work inside udev rules, copy /usr/lib/systemd/system/systemd-udevd.service to /etc/systemd/system/systemd-udevd.service and replace MountFlags=slave to MountFlags=shared.[[3]]("http://unix.stackexchange.com/a/154318") Keep in mind though that udev is not intended to invoke long-running processes. 

I thought that this would be the solution to my problems but udisks, as far as I can tell, would only work on specified drives and I can’t set more encompassing rules like with udev rules. The second idea to copy the file also seemed great but I couldn’t find the file in that location and the files with the same name never mentioned MountFlags. Compounding this, the default option for MountFlags is shared anyway, according to its manual (by typing ‘man system.exec’ in the terminal)

Some other references that may give you ideas on figuring this out:

From h[/SIZE][ttp://unix.stackexchange.com/questions/152485/mount-is-not-executed-when-called-by-udev/154318#154318]("http://unix.stackexchange.com/questions/152485/mount-is-not-executed-when-called-by-udev/154318#154318")[SIZE=2]:[/SIZE]
 [SIZE=2]
>  systemd-udevd runs in its own file system namespace and by default mounts done within udev .rules do not propagate to the host. To make your old scripts work you can set MountFlags=sharedin /usr/lib/systemd/system/systemd-udevd.service or (better) creating and editing its copy at /etc/systemd/system/

See man 5 systemd.exec for more information, MountFlags option. 

From [/SIZE][http://www.reactivated.net/writing_udev_rules.html#external-run](http://www.reactivated.net/writing_udev_rules.html#external-run): [SIZE=2]
> 
udev does not run these programs on any active terminal, and it does not execute them under the context of a shell. Be sure to ensure your program is marked executable, if it is a shell script ensure it starts with an appropriate [shebang]("http://en.wikipedia.org/wiki/Shebang_(Unix)") (e.g. #!/bin/sh), and do not expect any standard output to appear on your terminal.


 
Please help me Ubuntu forum users, you're my only hope![/SIZE]

---

### Post by him610 on 2016-08-03
You could use a USB stick with a *physical* write protect device on it.

---

### Post by gordintoronto on 2016-08-04
There are a couple of Linux distros which are specifically designed for kiosk operation. One of them might be a better choice for your application.

---

### Post by tychus2 on 2016-08-13
> **him610 said:**
> You could use a USB stick with a *physical* write protect device on it.

Thanks for the suggestion but my intention was to protect all media, including internal hard drives, from being written to by default.

> **gordintoronto said:**
> There are a couple of Linux distros which are specifically designed for kiosk operation. One of them might be a better choice for your application.

I did not know about kiosk distributions so will look into it, thanks.

I found a solution to the problem, from [http://serverfault.com/questions/766506/automount-usb-drives-with-systemd](http://serverfault.com/questions/766506/automount-usb-drives-with-systemd). I would have copied the code directly here but the forum software seems to lose line spacings when I do this. Credit goes to the original poster of the answer: Mike Blackwell. I modified his code slightly to deal with the fact it failed to mount volumes without FS labels.

The edited section of code was this originally:
```

[COLOR=#242729][FONT=Consolas]# Figure out a mount point to use
[/FONT][/COLOR]LABEL=${ID_FS_LABEL}
if /bin/grep -q " /media/${LABEL} " /etc/mtab; then
    # Already in use, make a unique one
    LABEL+="-${DEVBASE}"
fi
MOUNT_POINT="/media/${LABEL}"
```

I have changed it to this:
```

[COLOR=#242729][FONT=Consolas]# Figure out a mount point to use
[/FONT][/COLOR]LABEL=${ID_FS_LABEL}

[FONT=Calibri]# If the ID_FS_LABELis null or doesn't exist, use ID_FS_UUID.[/FONT]
[FONT=Calibri]if [ -z "${ID_FS_LABEL}" ]; then[/FONT]
[FONT=Calibri]    LABEL="${ID_FS_UUID}"[/FONT]
[FONT=Calibri]fi[/FONT]

if /bin/grep -q " /media/${LABEL} " /etc/mtab; then
    # Already in use, make a unique one
    LABEL+="-${DEVBASE}"
fi
MOUNT_POINT="/media/${LABEL}"
```
[/CODE]

Note that this answer will possibly not work on newer versions of Ubuntu at a later date (I'm using 14.06 (Xenial Xerus) 64-bit), as many other solutions provided didn't work, possibly due to changes with systemd over time. 

I hope that anyone else in a similar situation finds the solution I mentioned useful and that is saves you from days of trying to find the answer as it did me. Thanks to those who replied to my query.

---

