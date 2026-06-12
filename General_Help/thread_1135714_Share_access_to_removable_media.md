---
title: "Share access to removable media?"
date: 2009-04-24
forum: General Help
---

### Post by Githlar on 2009-04-24
I have made a couple of repository mirrors and stored them on an external hard drive. I've set up apache to work out of /var/www under the user www. I made a symlink in /var/www named i386 pointing to /media/Passport/Repos/i386/archive.ubuntu.com. Not to state the obvious, but theoretically, this should make it so I can access my repositories in this way: [http://localhost/i386/ubuntu](http://localhost/i386/ubuntu).

Why am I doing it this way instead of just adding a rule to sources.list? Well, I want to be able to use the packages already on my drive to download the jigdo-based images from cdimage.ubuntu.com. That way I can just point jigdo to [http://localhost/i386/ubuntu](http://localhost/i386/ubuntu) and get an image without even downloading anything extra.

Anyway, the problem is as follows: Apache will not follow the symlinks to my external. The problem is caused because apache is running as www, whereas my external HDD is mounted from FUSE under my main running user for access only by that user and root. I managed to fix this by adding an /etc/fstab rule mounting the external with the user option, but I don't like this method because it's not as smooth as using the HAL/FUSE daemon.

So, my question: How do I get FUSE (HAL?) to mount my external with shared permissions for root, my main user (who mounted it), and www? I tried opening Users/Groups settings for www and checked "Access external storage devices automatically" under the "User Privileges" tab and that didn't seem to to anything (nothing immediately anyway). I hesitate to restart unless I really have to, though I think perhaps that might have helped (Or restarting HAL/FUSE?).

Any input would be greatly appreciated.

---

### Post by bodhi.zazen on 2009-04-24
By default apache will not follow symlinks ;)

I advise you configure a virtualhost to do this task (following symlinks is a potential security risk).

Second, setting permissions is dependent on the file system, so FAT / NTFS are different from ext3/4.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Githlar on 2009-04-25
I knew somebody would say that. I had it in my post before and edited it out. I have Apache setup to follow symlinks in the directory. I got it to work by adding an fstab rule, however my goal is to avoid that and combine the simplicity of the Fuse interface with multi-user access. With an fstab rule I'd have to plug in the device, unmount it and then mount -a. Not very friendly if you ask me. This is, unless Fuse reads /etc/fstab rules? I'm not sure about that, but I can't test it at the moment.

Even if that is so, let's say I plug in multiple USB externals (which I do have multiple) in a different order every time. /dev/sdc1 (what would be in the fstab rule, for example) always refers to the first USB device I plugged in, so there's room for error if I had plugged in a different external than the one with my repositories. So I'd have to have multiple fstab entries - up to 4, one for each USB port - in order to get this to work and they all have to be the same permissions. Again, being as they're hotswappable USB drives this is kind of inconvenient. Is there no way to tell Fuse or Hald (whichever one makes the permissions for hotswappable drives) to share the drive with users in a certain group, perhaps?

This could probably all be resolved if I was using an ext filesystem with a UUID on my external, but I'd like to use this with Windows computers as well. After all, it is a 500G external and the repositories don't take up too much room on it.

EDIT: Wow, bodhi.zazen answered my post. I'm honored.

---

### Post by Githlar on 2009-04-25
Hmm. I'm not sure if it's what you originally planned, but I see in that link you gave me that it's possible to mount a disk based off label? I've been doing the Ubuntu thing for like 2 years and never knew that, haha. But perhaps adding an fstab rule via a label might work for me... It doesn't work right in my head, but we'll have to see. Thanks.

---

### Post by bodhi.zazen on 2009-04-25
If you want your USB devices to automout, put an entry in fstab by UUID or LABEL.

Then take a look at the package "usbmount"

```
sudo apt-get usbmount
```

Edit: :lolflag: - yes I help out the staff, but I still enjoy helping more then anything else I do.

---

### Post by Githlar on 2009-04-25
Yep, I set everything up with that label-based fstab rule and it seems to be working just fine. Thanks for pointing me in the right direction.

usbmount looks promising. Maybe I'll fool around with it later =D

---

