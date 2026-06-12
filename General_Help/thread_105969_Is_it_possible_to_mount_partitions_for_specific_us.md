---
title: "Is it possible to mount partitions for specific users only?"
date: 2005-12-19
forum: General Help
---

### Post by egon spengler on 2005-12-19
As I understand it, the fstab contains all of the settings for how and where to mount the various partitions. At some point during bootup **mount -a** is called which mounts all of the devices in the fstab (excluding those set to "noauto")

As this happens during boot I would assume that there is no way to only mount partition x if user y is logging in because nobody is logged in when mount -a is called.

The problem I have is that on a shared pc my samba shares are set to automount. Currently I have the uid and fmask/dmask settings in fstab give me alone rwx access to my shares. This works perfectly well but the share is still mounted and visible on everyone else's desktop.

Is there a way to hide this partition from other users? I thought at first perhaps a login script to mount only when I log in but as far as I can see that would require either sudo to mount it (and entering a password defeats the purpose of automounting) or allowing any user to mount which I'd rather not do to maintain the privacy of my files

Is there some way to achieve what I want?

---

### Post by frodon on 2005-12-20
If you set 700 rights and the owner to be your user only then only your user will be able to read the partition. However the partition will be still mounted.

---

### Post by Thunk on 2005-12-20
If you don't want it automatically mounted you can remove the mounting line from fstab and set a shortcut to the mounting command on your desktop. This way nobody would have it mounted but you.

---

### Post by egon spengler on 2005-12-23
I appreciate the feedback guys but as I said in my initial post I already have the partition mounted with 700 rights and am ideally looking for a solution that could facilitate auto mounting

---

### Post by kanem on 2005-12-29
Have you tried making the mountpoint in your directory? So in fstab instead of mounting the partition to /mnt/hda5 or whatever, point it to /home/you/mountpoint. Since other users can't go in your home folder they shouldn't be able to get to the partition.

---

### Post by egon spengler on 2005-12-31
That sounds like it might work kanem, the current mount point has read access for all so although I mount the share with 700 people can still see it exists, ~/ is 700 also so I would assume that it would mount invisibly to other users. Can't get to the shared pc to try it right now, but I definitely will give it a go

---

