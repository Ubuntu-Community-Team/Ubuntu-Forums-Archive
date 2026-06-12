---
title: "Copying Information onto Bigger Hard Drive"
date: 2006-04-28
forum: Desktop Environments
---

### Post by MadCowDzz on 2006-04-28
I'm looking at transitioning myself off of Ubuntu as my primary desktop and using it simply as a fileserver. I plan to SSH into the box, use Samba shares, etc.

As a part of this transition, I will be upgrading my hard drive. The Ubuntu machine currently contains two hard drives: 1x40GB and 1x200GB... both IDE. I think I mounted the 200GB as /home (but I'm not sure).

My goal is to replace the 200GB IDE with a 300GB SATA.

Now, this is where I'm looking for assistancce. I'm still new to Ubuntu and wouldn't know how to transition all the information. Is there any risk in doing this? How can I find out which hard drive is mounted where?

Thanks!

---

### Post by Ramses de Norre on 2006-04-28
You want to copy over your /home directory? That isn't that hard, cd to your home dir and execute this: ```
find . -depth -print0 | cpio --null --sparse -pvd /mnt/newhome/
```
assuming the new home is mounted on /mnt/newhome.
Then edit fstab to mount the new drive on /home instead of /mnt/newhome and log out and in.

---

### Post by MadCowDzz on 2006-04-28
My /etc/fstab reads as follow [excluding floppy and cdrom]:
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb2       /home           reiserfs defaults        0       2
/dev/hda5       none            swap    sw              0       0

Does this mean everything is stored on hda except /home?
And if, for whatever reason, I lose my second hard drive... only the home folder will be lost?

I know this is what I intended when I first installed Ubuntu... and now that I'm looking to replace the hard drive, I'd like to make sure.

I apologize for a relatively simple question, I just want to make sure.

Thanks!

---

### Post by Ramses de Norre on 2006-04-28
Everything but /home is on hda1, yes. But all your settings are stored in hidden folders in /home ;)

---

