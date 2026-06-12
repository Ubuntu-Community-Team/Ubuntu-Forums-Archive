---
title: "XOrg File"
date: 2009-02-14
forum: General Help
---

### Post by Illiniguy18 on 2009-02-14
Hi all,

I'm relatively new at this and need some help.  I attempted to edit my xorg file to increase my touchpad sensitivity on my laptop, but ran into a little trouble.  I restarted my computer for whatever reason, and now I cannot get into ubuntu anymore because the image is not loading or something like that.  So I need help with two things. First and most importantly, I need to somehow edit the xorg file and undo any changes I made because they are obvously wrong.  I'm thinking I need to access the ext3 file system in vista and then go from there, but I cannot find out how to do it.  I can see the Z drive in "My Computer", which is my ubuntu partition, but when I click on it, it says, "Do you want to format this disk?"  Is that what I want to do?  I'm afraid to format the disk.  Secondly, I need to address my initial problem of the mouse sensitivity.  It takes me 4-6 finger swipes to go across the screen, which is incredibly annoying.  I did a ton of searching on the forum and I was unable to find a solution.  If someone could help me out with these problems I would greatly appreciate it.  Thanks

---

### Post by k3rnelmustard on 2009-02-14
You could maybe access it from vista, or you could just use the livecd.  Did you try this? [http://www.fs-driver.org/](http://www.fs-driver.org/)  If this doesn't work, boot up the livecd and mount the drive.  If you don't know how to do this, post the output of ```
fdisk -l
``` here once you're in the livecd and I'll help you out.

---

### Post by Illiniguy18 on 2009-02-28
I was able to restore my xorg file using "sudo dpkg-reconfigure xserver-xorg".  However, my original problem remains where the touchpad on my laptop is not sensitive enough for my liking.  It takes roughly 4 swipes to get across the screen, and it is nowhere near as sensitive when in Windows.  If anyone could help me out that would be great.  Thanks

---

### Post by bodhi.zazen on 2009-02-28
well, the "problem" is that /etc/X11/xorg.conf is depreciated. By that I mean the ne xorg (xorg 7 +) is trying to make it "easier" and the theory is that all hard ware is now auto detected and works out of the box.

While this is great when it works, it is not so nice in that many, if not most, of the old edits to manually address these issues no longer work.

I am sure it will get better, but for now, when it does not work, it is a pain.

I suggest you do a google search on your touchpad + google or your lap top model + Linux, see if you can find a solution.

---

### Post by Illiniguy18 on 2009-02-28
The problem is that I have done a ton of searching.  One problem I have encountered is that I cannot save the xorg file when I edit it.  It says I do not have the permission to edit and save the file.  Why could that be?

---

### Post by bodhi.zazen on 2009-02-28
You have to edit the file as root.

First, always save a back  up you can restore if needed.

Then use 

```
gksu gedit /etc/X11/xorg.conf
```

And good luck, I have had mixed results with manual edits, 50/50 that they will work at best.

---

### Post by NJ0E on 2009-02-28
You'll need to be in root user or alternatley you can use sudo + your editing program + the xorgfile this will open your xorg file in an editor of your choice (your preference).  Then make your corrections/changes and then save the file.

---

