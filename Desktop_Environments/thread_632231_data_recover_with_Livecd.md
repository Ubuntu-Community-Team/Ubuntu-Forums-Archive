---
title: "data recover with Livecd"
date: 2007-12-05
forum: Desktop Environments
---

### Post by ksukat on 2007-12-05
Greetings,
Have a laptop of friend.  Its a Dell. She has gentoo on small partition and XP on bigger.  Well, backups didn't get done and now the windows partition is slightly borked.  Can boot to linux but not windows XP.  Can access Xp partition from Gentoo.  No sources for Gentoo so no way to add smb to kernel.  No samba to copy to windows machines on my network.

Downloaded LiveCD.  booted it up.  Created mount point /mnt/ntfs and mount -t ntfs /dev/sda2 /mnt/ntfs .  Worked ok.  Can access files.  Accessed windows machine with share on my network.  From terminal windows launched nautilus as root (to access mount).   Can create a folder on the windows share, but cannot copy from /mnt/ntfs to windows share (it just does nothing.  No error, nada).  Again, from ubuntu I can create a folder on the share.

Any ideas on how I can copy the data from the mounted partition to the windows share ?

thanks for any ideas.

---

### Post by nuke on 2007-12-05
The only reason I can think of (and I'm not as skilled as many in this forum) that the files are not copied is perhaps that you haven't set the read write option when you mounted the drive where you were copying recovered files.  I think the command includes "-ro".

I have been Linux for some years recovering "borked" Windows PCs.  I have found the best way to get lots of data off a Windows drive is to attach an external USB hard drive or USB key for small amount of files.

Or, if you have an ethernet connection, you could set up mail and email the files?

---

### Post by lswest on 2007-12-05
can you just share the mount point?  (e.g. right-click then choose "share folder")  otherwise  i agree with Nuke:P try that first

---

### Post by ksukat on 2007-12-05
Thanks for the quick reply.  But, I don't think 12GB is going to work with a usb key.  And I don't have a big enough external usb hard drive.

BTW, if you are using USB key, do you format it as NTFS and if so, how do you copy from LiveCD to it ?


btw: mount -t ntfs /dev/sda2 /mnt/ntfs   I don't think you can mount it rw.

---

### Post by ksukat on 2007-12-05
when I try to share the mount point, a box pops up saying "sharing services are not installed".  check the "samba to share..." box.  Tries to download samba and fails with the error:

"failed to fetch securitiy.ubuntu.com/......./samba_3.0.22-lubuntu3.1_i386.deb".

404 not found.

I abbeviated the exact message.

---

### Post by nuke on 2007-12-05
I think you can set mount ntfs as read write.  I can't remember off the top of my head.  Do a man mount.

How about using tar with gzip option and segment the file to the size of your usb key?  (Or find a external usb hard drive.  I seem to use them more and more.)  If you segment the file it will fill the USB, then pause, unmount the USB key, copy file off to another drive, remount USB key and resume.  This will take you more time than going to your local electronics store and buy an enclosure for a spare drive or buy an external drive.

You might look into burning a dvd if you have the memory on the PC and if the PC has a DVD driver???

---

### Post by ksukat on 2007-12-05
How can I burn a dvd (what steps).  Unit does have a dvd drive.

---

### Post by nuke on 2007-12-05
Maybe this link will help with the Read Write.  I kind of remember it being easier with the recent Ubuntu, but I also use SystemRecovery CD (if you can use the command line) and sometime Knoppix.

How to mount ntfs
[http://ubuntuforums.org/archive/index.php/t-1886.html](http://ubuntuforums.org/archive/index.php/t-1886.html)

---

### Post by az on 2007-12-05
> **ksukat said:**
> when I try to share the mount point, a box pops up saying "sharing services are not installed".  check the "samba to share..." box.  Tries to download samba and fails with the error:

"failed to fetch securitiy.ubuntu.com/......./samba_3.0.22-lubuntu3.1_i386.deb".

404 not found.

I abbeviated the exact message.

When you try to enable sharing, the live cd will try to connect to the internet to install the samba packages.  If you are not connected to the net, this will not happen.

A simpler option would be to install the ssh-server package.  You can download the package here:
[http://packages.ubuntu.com/gutsy/net/openssh-server](http://packages.ubuntu.com/gutsy/net/openssh-server)

and then connect to the machine using a file transfer client like filezilla on the remote machine.  Copy the files that way.

---

### Post by ksukat on 2007-12-05
Well,
I unmounted /mnt/ntfs.

I added to /etc/fstab:
/dev/sda2 /mnt/ntfs ntfs ro,dmask=0222,fmask=0333 0 0

then did a mount /mnt/ntfs.

Then as default user I could copy files from /mnt/ntfs to the windows share on my network.

So, thanks for all the help, I really appreciate it.

---

