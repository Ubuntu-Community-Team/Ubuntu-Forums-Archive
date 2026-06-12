---
title: "cannot mount volume (internal ext3) after canceled disk check"
date: 2009-04-08
forum: General Help
---

### Post by raydar on 2009-04-08
I have two hard disks in my desktop machine running Ubuntu 8.10, and yesterday, at boot, the non-booting disk came due for a routine disk check.  I was in a hurry, so I canceled it.  Since then, that non-booting disk does not mount anymore on boot, and I can't "sudo nautilus" my way to it either; desktop wallpaper failed to load because it's on that drive, and the icons on my desktop that link to locations on that drive are accompanied by both "lock" and "red x" icons (the links being broken).  The "Places" menu retains its link to the drive, but when I select it, I get two error boxes:

"Cannot mount volume. You are not privileged to mount this volume."

followed, a few seconds later, by:
  
"DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

I've seen other threads here about ntfs volumes, and this isn't ntfs; it's a Linux drive (that I used to boot from several Ubuntu versions ago; it still has Gutsy installed).  

I've also seen the other threads mentioning this problem's occurring after an update, and there have been several updates recently, so I can't rule that out as a possibility, but I first noticed the problem immediately after canceling the startup disk check.

Is there an automatic way to get it to mount automatically again, with all my links reconnected?  Like fsck perhaps?

Thanks!

---

### Post by cariboo on 2009-04-08
Seeing as you can't mount the drive, why not open a terminal and run fsck on it. 

```
sudo fsck -a /dev/sdb
```

This should repair the problems.

Jim

---

### Post by raydar on 2009-04-08
Thanks, cariboo907.

Weird:  If I do "sudo fsck -a /dev/sdb" I get

[INDENT]fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb
/dev/sdb: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
[/INDENT]

When I look in /etc/fstab, though, I see mention of sdb1, so I tried "sudo fsck -a /dev/sdb1" and got

[INDENT]fsck 1.41.3 (12-Oct-2008)
/dev/sdb1: clean, 163701/29769728 files, 55956139/59528849 blocks
[/INDENT]

I also booted up as root and tried just plain "fsck -a", which showed clean volumes.

After booting back into the regular GUI, I opened a terminal and did "sudo fsck -a"; this got me my first sign that the system might have discovered a problem:

[INDENT]
fsck 1.41.3 (12-Oct-2008)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sda1: recovering journal
/dev/sda1: clean, 226400/2342912 files, 7912410/9357854 blocks
/dev/sdb1: clean, 163701/29769728 files, 55956139/59528849 blocks
[/INDENT]

And when I rebooted, an "unclean shutdown" disk check was commenced.

None of it helped, though; I'm still unable to mount my other Linux volume.  I can boot from it, or begin to--I seem to have deleted some files necessary for a complete boot (I get past the 7.10 splash screen, and the progress bar goes all the way across very slowly, but then the boot gets stuck).

(One interesting thing--not sure how it could be related--is that when I try to boot into recovery mode, I'm unable to select most of the options, including the fsck option; I get a line of text saying "loading [N-something] server" and am returned to the menu every time I tab to OK and hit enter.)

It seems the volume in question is readable, since I can boot from it, but why on earth can't I mount it?  Any further suggestions?  Couldn't have anything to do with the fact I have a folder on that drive set as my Documents folder, could it?

---

### Post by raydar on 2009-04-09
Wow, I should've heeded the warning about running fsck on a mounted volume:  Next time I booted, a manual fsck was forced, and I lost a bunch of files on my heretofore "good" drive (bad idea to have an e-mail client open while running fsck; I should've known better).  

Boy, all this from cancelling a routine disk check!

---

