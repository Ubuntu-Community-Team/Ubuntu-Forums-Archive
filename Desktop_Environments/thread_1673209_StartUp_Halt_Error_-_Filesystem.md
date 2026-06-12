---
title: "StartUp Halt Error - Filesystem"
date: 2011-01-22
forum: Desktop Environments
---

### Post by miserly-martyred on 2011-01-22
I just accidentally clicked on my ubuntu drive when I was in PCBSD Unix and I had somehow glanced at a few things.  When I tried, it didn't really let me in as much, but it said something about an access error and denial when I looked with the KDE Dolphin file browser.

All I did was leave the rest alone and reboot but then got this when attempting to access Ubuntu:
----------
init: hwclock main process (366) terminated with status 29564.

General error mounting file systems.
----------
I also got back into BSD and formally unmounted and rebooted again, but to no avail.

Any thoughts on my recent success as a moron?

---

### Post by miserly-martyred on 2011-01-22
on second thought, better make that error read as follows:

"... terminated with status 295c4."

def. not a "6" there...

---

### Post by miserly-martyred on 2011-01-22
As some additional notes, I am denied the ability to do the following upon reboot/power on to ubuntu:

fsck
su myusername
nautilus
mountall start

on top of that, I managed to boot an Ubuntu LiveCd and I could access things perfectly for viewing.  I then proceeded to try and use the "ecryptfs-mount-private.desktop" file feature and that did not work.

That ".desktop" also failed when I did a cd to the file system to which it pertained.

The Ubuntu LiveCd is now the only thing that can view the HDD's files at all.

Since the LiveCd worked, I thought that the mount/unmount it would do on the HDD would help, but even though it works much better than the mount/unmount with BSD, it still did not clean it up for reboot.

I additionally noticed that when I browse the affected HDD, in "dev" I lack anything to the nature of [disk] --> [by id] , etc.  I don't know what that is meaning, there is a ton of other stuff in dev, but I'm wondering if the "existence" of my drives is null somehow.

LinuxReader, by DiskInternals, also failed to browse the Linux HDD with Ubuntu on it.

ugh ...

---

### Post by miserly-martyred on 2011-04-04
I've been gettin' quite a few, "unable to do xyz because your home directory is not setup correctly" errors.

I used the official Ubuntu guide about encrypted directories and I followed the procedures about recovering the mount passphrase.

I have the passphrase file, the system just refuses to accept the entry procedure for me to get my data.

Any advice on "corrupted" home directories?  I haven't even meddled with the directory that much :(

---

