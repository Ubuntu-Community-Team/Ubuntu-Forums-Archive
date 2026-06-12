---
title: "Alternate way to edit files?"
date: 2009-06-14
forum: General Help
---

### Post by Darkness Falls on 2009-06-14
I fear I may have done something rather unfortunate. I'm a week and a half into my first experiences with Ubuntu (and GNU/Linux in general) running a relatively fresh installation of Jaunty on my laptop, with a couple of modifications (most importantly, the *linux-backports-modules-jaunty* package, along with a few others related to ALSA that were recommended on this site). The two main things that didn't work with it were the wireless and the sound; having managed to get the wireless working, I've been playing around with the *alsa-base.conf* file, following some of the recommendations in the Multimedia & Video forum sticky thread. Sadly, the last lines I added to it seem to have caused a fatal problem; Ubuntu now hangs partway through the startup procedure, and won't finish loading. Even Recovery Mode seems to have this problem - it prints a lot of text to the screen, too fast (and needing way more understanding than I have) to follow, and then stops inexplicably, leaving me without even a prompt. I can then type things in, but I don't know what commands to use, and hitting enter seems to produce no result other than a new line to type on, regardless of what I type.

I figured if I could undo the changes, I might be able to get Ubuntu to load again, so I tried looking for the *alsa-base.conf *file through Vista (I'm running a dual-boot system), but Vista doesn't appear to recognise the partition that Ubuntu's installed on, so no luck there. I then thought to try booting from the Ubuntu CD and trying to edit it that way, but, despite the bios saying Boot From CD is enabled, and the CD drive coming before the hard drives in the list, it won't load from the CD - GRUB loads instead, offering me the usual choice between Ubuntu and Vista. I don't even know if what I'm trying is possible from the CD, as presumably the *sudo* command will want the password of my hard-disc installed version to proceed, but it's all I could think to do.

Is there any way to access it, or have I pretty much messed up my laptop? If so, how do I get to it to make the changes? If I've messed it up totally, is there any way I can get my laptop to recognise the CD drive again so I can reformat the partition and reinstall Ubuntu?

D.F.

---

### Post by KhurramM on 2009-06-14
If u intend to use the liveCD to undo what u did,

then in the bios, u have to see the boot sequence,

Remove your hard from the boot sequence, then only cdrom will boot the CD.

Hope this helps.

---

### Post by Zill on 2009-06-14
Darkness Falls:  As KhurramM has already advised, you should be able to run the live CD if you set your BIOS options correctly to run the CD first.

One "top tip" that you may find useful in future is to *always* make a backup copy of a config file *before* you make any changes to it. eg.

```
sudo cp filename.conf filename.conf_original
```

Then, if you have any problems with your edited file, it is a relatively simple matter to boot into your live CD and replace your edited file with the original version. eg.

```
sudo cp filename.conf_original filename.conf
```

---

### Post by CatKiller on 2009-06-14
> **Darkness Falls said:**
> I don't even know if what I'm trying is possible from the CD, as presumably the *sudo* command will want the password of my hard-disc installed version to proceed, but it's all I could think to do.

It's perfectly possible, and you certainly wouldn't be the first to use the live cd to rescue a broken system. It's part of what they were invented for.

But sudo won't want the password of your hard-drive install; it doesn't know what that is. It would require the password of the user for the environment that's running - in this case the user *ubuntu*. That user doesn't have a password, so sudo won't ask you for one.

Good luck!

---

### Post by Darkness Falls on 2009-06-16
Excellent - thanks for your help, everyone! I managed to run the CD and edit things back to the way they were before; it seemed to try to edit the *alsa-base.conf* file on the CD-version in preference to the one on the hard drive, but I navigated to the file on the hard disk in the terminal and tried it again, and that fixed it.

Thanks for your suggestions - I'll take a backup copy in future before trying any further adjustments!

D.F.

---

