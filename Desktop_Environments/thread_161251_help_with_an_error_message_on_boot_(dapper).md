---
title: "help with an error message on boot (dapper)"
date: 2006-04-16
forum: Desktop Environments
---

### Post by sal on 2006-04-16
i keep getting an error message on boot. something along the lines of "mkdir /dev/shm/var.lock failed" or something along those lines. there is about four lines of the message. the problem is i can't read the whole thing because it go's by to fast.

so, is there a way in kubuntu dapper 6.06 to create a log of all messages that apear on boot? 

thanks in advance.

---

### Post by babalou on 2006-04-16
[QUOTE=sal]the problem is i can't read the whole thing because it go's by to fast.
[/QUOTE]
You could always pause the boot process by using Ctrl+S (same to resume boot)

[QUOTE=sal]so, is there a way in kubuntu dapper 6.06 to create a log of all messages that apear on boot? 
[/QUOTE]
Go to /etc/default/ and edit file "bootlogd". Inside that file, turn the boot logging flag on ("BOOTLOGD_ENABLE=Yes").
Check that bootlogd is called at startup (bootlogd symbolic link present under rcS.d dir). If not (my case), run the following to add/stop boot daemon automatically:
sudo ln -s /etc/init.d/bootlogd /etc/rcS.d/S00bootlogd
sudo ln -s /etc/init.d/bootlogd /etc/rc0.d/K00bootlogd
sudo ln -s /etc/init.d/bootlogd /etc/rc6.d/K00bootlogd

All messages will be logged under /var/log/boot

yb

---

### Post by sal on 2006-04-16
here is the error message im getting on boot:
Sun Apr 16 15:53:39 2006: mkdir: cannot create directory `/dev/shm/var.run': Read-only file system
Sun Apr 16 15:53:39 2006: mkdir: cannot create directory `/dev/shm/var.lock': Read-only file system
Sun Apr 16 15:53:39 2006: mount: mount point /dev/shm/var.run does not exist
Sun Apr 16 15:53:39 2006: mount: mount point /dev/shm/var.lock does not exist
Sun Apr 16 15:53:39 2006: mount: special device /dev/shm/var.run does not exist
Sun Apr 16 15:53:39 2006: mount: special device /dev/shm/var.lock does not exist
Sun Apr 16 15:53:39 2006: rmdir: /dev/shm/var.run: No such file or directory
Sun Apr 16 15:53:39 2006: rmdir: /dev/shm/var.lock: No such file or directory

dose anyone know how to fix it?

thanks.

---

### Post by babalou on 2006-04-16
Can you give more info about the error (more logging line and not only the actual error).

What is the content of your /etc/fstab file. Looks like your shared memory filesystem is not mounted correctly or is pointing to a not supported filesystems for read/write operation (eg. NTFS)?

yb

---

### Post by sal on 2006-04-17
[QUOTE=babalou]Can you give more info about the error (more logging line and not only the actual error).

What is the content of your /etc/fstab file. Looks like your shared memory filesystem is not mounted correctly or is pointing to a not supported filesystems for read/write operation (eg. NTFS)?

yb[/QUOTE]

here is what my fstab looks like:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       none            swap    sw              0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hdb1       /mnt/120gb      ext3    defaults        0       3
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
tmpfs           /dev/shm        tmpfs   defaults,ro     0 0

---

### Post by babalou on 2006-04-17
[QUOTE=sal]here is what my fstab looks like:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
tmpfs           /dev/shm        tmpfs   defaults,ro     0 0[/QUOTE]
You mount your tmpfs filesystem read-only ...
Entry in fstab should be more like:
tmpfs /dev/shm tmpfs defaults 0 0 

yb

---

### Post by sal on 2006-04-17
ok i changed it to look like your example and now this is what i get on boot:

Mon Apr 17 06:28:56 2006: ^[[74G[ ok ]
Mon Apr 17 06:28:56 2006: ^[[74G[ ok ]iles needed to boot...       ^[[80G 
Mon Apr 17 06:28:56 2006: ^[[74G[ ok ]ring restricted drivers...       ^[[80G 
Mon Apr 17 06:28:56 2006: ^[[74G[ ok ]basic networking...       ^[[80G 
Mon Apr 17 06:28:56 2006: ^[[74G[ ok ]kernel event manager...       ^[[80G 
Mon Apr 17 06:28:56 2006: ^[[74G[ ok ]ardware drivers...       ^[[80G 
Mon Apr 17 06:28:56 2006:  * Starting PCMCIA services...       ^[[80G  * PCMCIA not present
Mon Apr 17 06:28:56 2006: ^[[74G[ ok ]anual drivers...       ^[[80G 
Mon Apr 17 06:28:56 2006:  * Checking root file system...       ^[[80G e2fsck 1.38 (30-Jun-2005)
Mon Apr 17 06:28:56 2006: /: clean, 148631/1221600 files, 1373551/2441880 blocks
Mon Apr 17 06:28:56 2006: ^[[74G[ ok ]
Mon Apr 17 06:28:56 2006: ^[[74G[ ok ]RAID devices...       ^[[80G 
Mon Apr 17 06:28:57 2006: ^[[74G[ ok ]p LVM Volume Groups...       ^[[80G 
Mon Apr 17 06:28:57 2006: ^[[74G[ ok ]Enterprise Volume Management System...       ^[[80G 
Mon Apr 17 06:28:58 2006: e2fsck 1.38 (30-Jun-2005)
Mon Apr 17 06:28:58 2006: /home: clean, 4082/1028160 files, 114444/2054311 blocks
Mon Apr 17 06:28:58 2006: e2fsck 1.38 (30-Jun-2005)
Mon Apr 17 06:28:58 2006: /dev/hdb1: clean, 5396/14663680 files, 14007811/29304560 blocks
Mon Apr 17 06:28:58 2006: mount: special device /dev/shm/var.run does not exist
Mon Apr 17 06:28:58 2006: mount: special device /dev/shm/var.lock does not exist
Mon Apr 17 06:28:58 2006: rmdir: /dev/shm/var.run: No such file or directory
Mon Apr 17 06:28:58 2006: rmdir: /dev/shm/var.lock: No such file or directory
Mon Apr 17 06:28:58 2006: ^[[74G[ ok ]3 on /home type ext3 (rw))...       ^[[80G 
Mon Apr 17 06:29:00 2006: ^[[74G[ ok ]ng network interfaces...       ^[[80G 
Mon Apr 17 10:28:59 2006: ^[[74G[ ok ]ng up general console font...       ^[[80G 
Mon Apr 17 10:28:59 2006:  * Setting up per-VC fonts...       ^[[80G  * /dev/tty2
Mon Apr 17 10:28:59 2006:  * /dev/tty3
Mon Apr 17 10:28:59 2006:  * /dev/tty4
Mon Apr 17 10:28:59 2006:  * /dev/tty5
Mon Apr 17 10:29:00 2006:  * /dev/tty6
Mon Apr 17 10:29:00 2006: ^[[74G[ ok ]
Mon Apr 17 10:29:00 2006:  * Entering runlevel: 2
Mon Apr 17 10:29:00 2006: cat: /var/lib/acpi-support/system-manufacturer: No such file or directory
Mon Apr 17 10:29:00 2006: cat: /var/lib/acpi-support/system-product-name: No such file or directory
Mon Apr 17 10:29:00 2006: cat: /var/lib/acpi-support/system-version: No such file or directory
Mon Apr 17 10:29:00 2006: ^[[74G[ ok ]CPI modules...       ^[[80G 
Mon Apr 17 10:29:00 2006: ^[[74G[ ok ]ACPI services...       ^[[80G 
Mon Apr 17 10:29:00 2006: ^[[74G[ ok ]system log daemon...       ^[[80G 
Mon Apr 17 10:29:00 2006: ^[[74G[ ok ]kernel log daemon...       ^[[80G 
Mon Apr 17 10:29:00 2006: ^[[74G[ ok ]system message bus dbus       ^[[80G 
Mon Apr 17 10:29:00 2006: ^[[74G[ ok ]Hardware abstraction layer hald       ^[[80G 
Mon Apr 17 10:29:03 2006: Starting APC UPS power management: apcupsd.
Mon Apr 17 10:29:03 2006: ^[[74G[ ok ]Common Unix Printing System: cupsd       ^[[80G 
Mon Apr 17 10:29:04 2006: ^[[74G[ ok ]HP Linux Printing and Imaging System       ^[[80G 
Mon Apr 17 10:29:05 2006: ^[[74G[^[[31mfail^[[39;49m]bootlogd       ^[[80G 
Mon Apr 17 10:29:05 2006: ^[[74G[ ok ]DirMngr dirmngr       ^[[80G 
Mon Apr 17 10:29:05 2006: Starting the Firestarter firewall: done.
Mon Apr 17 10:29:06 2006: Starting GKrellM monitoring daemon: gkrellmd.
Mon Apr 17 10:29:06 2006: ^[[74G[ ok ]isc parameters...       ^[[80G 
Mon Apr 17 10:29:08 2006: ^[[74G[ ok ]Postfix Mail Transport Agent postfix       ^[[80G 
Mon Apr 17 10:29:09 2006: ^[[74G[ ok ]RAID monitoring services...       ^[[80G 
Mon Apr 17 10:29:09 2006: ^[[74G[ ok ]anac(h)ronistic cron: anacron       ^[[80G 
Mon Apr 17 10:29:09 2006: ^[[74G[ ok ]deferred execution scheduler...       ^[[80G 
Mon Apr 17 10:29:09 2006: ^[[74G[ ok ]periodic command scheduler...       ^[[80G 
Mon Apr 17 10:29:09 2006: ^[[74G[ ok ]additional executable binary formats binfmt-support       ^[[80G 
Mon Apr 17 10:29:10 2006: Starting K Display Manager: kdm.
Mon Apr 17 10:29:10 2006: ^[[74G[ ok ]ocal boot scripts (/etc/rc.local)       ^[[80G

---

### Post by babalou on 2006-04-17
[QUOTE=sal]
Mon Apr 17 06:28:58 2006: mount: special device /dev/shm/var.run does not exist
Mon Apr 17 06:28:58 2006: mount: special device /dev/shm/var.lock does not exist
Mon Apr 17 06:28:58 2006: rmdir: /dev/shm/var.run: No such file or directory
Mon Apr 17 06:28:58 2006: rmdir: /dev/shm/var.lock: No such file or directory
[/QUOTE]

does /dev/shm exist on your system?
```

ls -al /dev/shm

```

---

### Post by sal on 2006-04-17
[QUOTE=babalou]does /dev/shm exist on your system?
```

ls -al /dev/shm

```[/QUOTE]

this is the output of the command:

ls -al /dev/shm
total 0
drwxrwxrwt  2 root root    40 2006-04-17 06:28 .
drwxr-xr-x 16 root root 14780 2006-04-17 10:29 ..

---

### Post by babalou on 2006-04-17
Have you ever created this mounting point by running 
```
mkdir /dev/shm 
```

---

### Post by sal on 2006-04-17
[QUOTE=babalou]Have you ever created this mounting point by running 
```
mkdir /dev/shm 
```[/QUOTE]

no, but there is an /dev/shm directory on my system.

---

### Post by irober02 on 2006-07-22
I've got a similar situation. I did not expressly create /dev/shm nor change it's ownerships or permissions. I think it is the product of the installation procedure. On my installation, /dev/shm is not mentioned in /etc/fstab but it is listed in /etc/mtab. (devshm /dev/shm tmpfs rw 0 0)

---

### Post by Ogre the Horrible on 2006-09-26
I am having the same issue....

I belive the problem is caused in the startup scripts in rcS.d, particularly S35mountall.sh.  In that script it calls functions in /lib/init/functions.sh.

Relevant parts of /lib/init/functions.sh
```
#
#
# Preserve /var/run and /var/lock mountpoints
#
pre_mountall ()
{
        # We may end up mounting something over top of /var, either directly
        # or because /var is a symlink to something that's mounted.  So keep
        # copies of the /var/run and /var/lock mounts elsewhere on the root
        # filesystem so they can be moved back.
        mkdir /dev/shm/var.run /dev/shm/var.lock
        mount -n --bind /var/run /dev/shm/var.run
        mount -n --bind /var/lock /dev/shm/var.lock
}

#
# Restore /var/run and /var/lock mountpoints
#
post_mountall ()
{
        # Make sure the new filesystem has a /var/run and /var/lock
        [ -d /var/run ] || mkdir /var/run
        [ -d /var/lock ] || mkdir /var/lock

        # Move the mountpoints back.  Fortunately mount seems to not care
        # if these are the same thing (ie. /var didn't get changed) so we
        # do this regardless
        mount -n --move /dev/shm/var.run /var/run
        mount -n --move /dev/shm/var.lock /var/lock

        # Clean up after ourselves
        rmdir /dev/shm/var.run /dev/shm/var.lock
}

```

So it appears that even though the scripts are supposed to create the necessary directories, they are not being created.  I have just turned on boot logging....to see if there are any errors prior to the "device not found" error....

---

### Post by lambda379 on 2007-11-22
Has anyone solved this error?  It seems for Gutsy, S35mountall.sh calls /lib/init/mount-functions.sh. Which contains the script outlined in "Ogre the Horrible" latest post.  

On each boot I get errors:
mkdir cannot create directory '/dev/shm/var.run' file exists
mkdir cannot create directory '/dev/shm/var.lock' file exists
rmdir '/dev/shm/var.run' device or resource busy
rmdir '/dev/shm/var.lock' device or resource busy

---

### Post by Peter09 on 2007-11-29
I have exactly the same problem on my desktop machine - any solutions yet?

---

### Post by Ogre the Horrible on 2007-12-23
Even though I have almost completely stopped using Ubuntu, the way I was able to fix this error was to make sure that var was *NOT* a separate partition....as soon as it was just a directory on the root partition, the error went away.  Example : root partition used to be /dev/sdb5 and var was /dev/sdb10.  Once I moved var to a directory on the root partition and removed /dev/sdb10 from Ubuntu's knowledge, the error just went away.  Hope this helps

---

