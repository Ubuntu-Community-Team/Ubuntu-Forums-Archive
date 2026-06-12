---
title: "Mounting a linux partition"
date: 2005-11-28
forum: Desktop Environments
---

### Post by Zarkoth on 2005-11-28
For the past two weeks or so, my computer has been going through a steady decline...  First, the internet cuts out, no explaination whatsoever, neither XP or Ubunutu can connect...  Then, when I log on, I get this message from my monitor - "Video mode not supported"  For a while, i could just log in from memory, and it all worked fine...except for the internet, of course.  But then, it stopped letting me log in.  

So basically, my computer was steadly growing into a state which i like to call "tanked".  I declared it tanked when I started it up and it decided that due to internal errors, it couldn't start the X graphical server...or something.  But yes, it was tanked.  In that, my computer has just had the equivalent of a 105mm tank round being shot through it.  Hehe, i like that analogy.

I'll try that sometime.

Anywho, I decided to rescue my files and do a nice and definitive re-install.  At first I was hoping I could master the command line (whose power I've grown to appreciate over the past few months) and do it there.  I'll hopefully be able to do that later, but currently I've yet to be weaned off the GUI teat.

So I decided to burn a Breezy live CD, mount my partitions, and just copy all my home files to a safe partition that XP and Ubuntu share, because they can be friends sometimes.

Alas, I dug up the printed version of a tutorial on how to mount various partitions on Ubuntu from the wiki.  It has me download a script that should do it, and also offers manual instructions.  The script doesn't work, but the manual instructions work just fine, by guiding me through what to edit on /etc/fstab.

So after hitting "sudo gedit /etc/fstab"  and entering

```

/dev/hda2   /media/windows     vfat       user,fmask=0111,dmask=0000   0      0

```

At the end of the file, my safe partition is mounted.  The only thing is, i haven't managed to mount the Linux partition I need so I can rescue my files...

These files are quite dear to me, and I really don't want to have to go through another tearful goodbye.:(   So what would I enter for my linux partition? (which, under normal circumstances, was "/dev/hda3")

Thanks in advance!

---

### Post by aysiu on 2005-11-28
Even though Ubuntu has a live CD, it's not really intended to be a recovery CD (you'd be better off with Knoppix), but since you already have it, let's use it.

The simplest way is to figure out what the partition is called. To do that type ```
sudo fdisk -l
``` Let's say, for argument's sake, that it's /dev/hda3 and type Ext3. Then ```
sudo mkdir /recovery
sudo mount -t ext3 /dev/hda3 /recovery
gksudo nautilus
``` Then find the "recovery" folder.

---

### Post by Brent Dax on 2005-11-28
[QUOTE=Zarkoth]These files are quite dear to me, and I really don't want to have to go through another tearful goodbye.:(   So what would I enter for my linux partition? (which, under normal circumstances, was "/dev/hda3")[/QUOTE]
Unless I'm misunderstanding, you should be able to do "mount /dev/hda3 /mount/point", replacing "/mount/point" with the actual directory you want to mount the drive on.  If you want to use /etc/fstab, the entry should be something like "/dev/hda3 /mount/point ext3 defaults 0 0".

---

### Post by Zarkoth on 2005-11-28
Thanks!  It worked just fine, and all my files are saved and prancing happily through the field of.....hda2, I'm running my re-install and all goes well!

Gotta love that linux community!

---

