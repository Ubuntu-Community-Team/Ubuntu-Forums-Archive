---
title: "Graphical Mount Command"
date: 2019-11-08
forum: Desktop Environments
---

### Post by MOGuy78 on 2019-11-08
Does anyone know of a good graphical front-end for the USB mount command?

---

### Post by tea for one on 2019-11-09
**gnome-disks** is a graphical utility.

However, after inserting a USB device, you'll find that it is probably already mounted.

**gnome-disks** will then give you the opportunity to mount and unmount as you wish.

---

### Post by TheFu on 2019-11-09
> **MOGuy78 said:**
> Does anyone know of a good graphical front-end for the USB mount command?

Nope. At least not any that use "real" mounts. All the graphical tools seem to use Gnome gvfs/gio methods which behave poorly and have unsatifactory performance, IMHO.  If you use a file manager to magically access storage, almost in every case it will be using some slow, Gnome, FUSE, driver.  Yuck.

The only ways I know to get a mount using a kernel driver is to use
[LIST=1]
[*]fstab
[*]autofs
[*]manual mount command from a terminal.
[/LIST]
Sorry.

Especially with storage that uses foreign file systems like NTFS or FAT-whatever, having full control over the mount options and performance settings is highly desirable. Security is the main reason for these choices/options.

```
NAME
       fusermount - unmount FUSE filesystems

SYNOPSIS
       fusermount [OPTIONS] MOUNTPOINT

DESCRIPTION
       Filesystem  in  Userspace  (FUSE)  is a simple interface for userspace
       programs to export a virtual filesystem to the Linux kernel.  It  also
       aims to provide a secure method for non privileged users to create and
       mount their own filesystem implementations.

       fusermount is a program to unmount FUSE filesystems.

```
The **fusermount** command can easily be scripted, but for USB storage, I find it much more convenient to use **autofs** so I have control over the mount performance and security options.

**Update:** I took a look at Gnome disks.  There is a gear/settings option for each file system discovered. In those options, it is possible to add mount options - NICE!  Also, it is possible to choose a different mount location and if the "mount at startup" checkbox is selected and permissions allow, it will add the mount to the fstab.  
```
sudo -H gnome-disks
``` to get the correct authorization.  Don't just use sudo alone.

---

### Post by MOGuy78 on 2019-11-10
I'm sorry, but I didn't explain my situation very well.  I found an old Gateway 1.6ghz that I had lying around my house, and I just wanted a simple computer I could use for web browsing and to listen to music on.  Since I needed a fairly light-weight OS, I installed lxqt desktop, and am using midori web browser, xfe file manager, and a simple audio player.
So far, it seems to be working great, but one of the few problems that I'm having is that it doesn't seem to auto-mount my USB flash drives.  I really don't want to mess with using the terminal, especially when working with sudo.  I've been looking around online, and it seems like Udiskie may be what I'm looking for.  I saw where the Gnome-disks app would work well, but as it seems to be heavy on memory, as well as that I'm not using Gnome, I doubt that would work for me.
As I said, I'd rather not mess with the cli, so would Udiskie be a good choice for my needs?  or are there other GUI apps that I haven't considered?  Thanks in advance.

---

### Post by TheFu on 2019-11-10
Don't fear the shell.  There is no lighter solution.

---

### Post by tea for one on 2019-11-10
**Xfe** file manager is a new one for me so I had a look at the homepage where it states:-

> Mount/Unmount devices (for Linux only)
Warn when mount point are not responding (Linux only)

Do your usb devices not appear in the file manager window when you plug them into your PC?

Which operating system did you install?

---

