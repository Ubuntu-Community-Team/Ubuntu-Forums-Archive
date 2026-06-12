---
title: "How do I mount partition after unclean shutdown?"
date: 2009-03-11
forum: General Help
---

### Post by matt.r.murray on 2009-03-11
Hi, 
I have had a problem with my work laptop (Dell Inspiron) after shutting down in hibernation mode with Windows XP. When I reboot I get "Disk Read Error - Please restart" error message. So of course, restarting does nothing.

I tried to diagnose the problem using a Ubuntu 8.04 Live CD. The system says that I cannot mount the volume /dev/sda1 as it is in hibernation mode. So here is what I tried:

[INDENT]1. sudo mount -t ntfs-3g /dev/sda1 /mnt
Windows is hibernated - suggests remove_hiberfile

2. sudo mount -t ntfs-3g /dev/sda1 /mnt -o remove_hiberfile
$LogFile indicates unclean shutdown - suggests force mount

3. sudo mount -t ntfs-3g /dev/sda1 /mnt -o force
Windows is hibernated and refuses to mount - suggests remove_hiberfile. And the cycle continues.

4. I can mount the volume as read only and all the data is there. Just untouchable. 
sudo mount -t ntfs-3g /dev/sda1 /mnt -o ro
[/INDENT]
I really need some help with this as the work laptop contains my thesis which is due at the end of the month!!

Thanks,
Matt.

FYI, here are the commands from the terminal. 

[INDENT]**ubuntu@ubuntu~$ sudo mount -t ntfs-3g /dev/sda1 /mnt**
Windows is hibernated, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, or mount the volume read-only with the 'ro' mount option, or
mount the volume read-write with the 'remove_hiberfile' mount option.
For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /mnt -o remove_hiberfile

**ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda1 /mnt -o remove_hiberfile**
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /mnt -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /mnt ntfs-3g force 0 0
**ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda1 /mnt -o force**
Windows is hibernated, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, or mount the volume read-only with the 'ro' mount option, or
mount the volume read-write with the 'remove_hiberfile' mount option.
For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /mnt -o remove_hiberfile

**ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda1 /mnt -o ro**[/INDENT]

---

### Post by dcstar on 2009-03-11
> **matt.r.murray said:**
> Hi, 
I have had a problem with my work laptop (Dell Inspiron) after shutting down in hibernation mode with Windows XP. When I reboot I get **"Disk Read Error** - Please restart" error message. So of course, restarting does nothing.
........

That sort of error indicates a problem with your drive and/or XP install, and mucking around with Ubuntu is unlikely to resolve that.

Find a Windows recovery CD (do a Google search) and try that. This is not an Ubuntu issue, it is a Windows issue.

---

