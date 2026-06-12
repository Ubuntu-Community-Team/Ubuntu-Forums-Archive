---
title: "Nautilus Desktop - Icons"
date: 2009-05-14
forum: Desktop Environments
---

### Post by PureLoneWolf on 2009-05-14
Hi all

I am wondering if this is possible.  I have permanently mounted my external hard disks through fstab and told Nautilus that I don't want to see volume icons...as I don't want it displaying all of my (already mounted) hard disks.

However, I would like it to place the CD/DVD/USB/Ipod icon on the desktop as and when I insert them.

Is this possible?

Thanks

---

### Post by coffeecat on 2009-05-14
> **PureLoneWolf said:**
> I have permanently mounted my external hard disks through fstab and told Nautilus that I don't want to see volume icons...as I don't want it displaying all of my (already mounted) hard disks.

When you say, "told Nautilus", do you mean through gconf-editor?

Anyway, do you mount your external discs in /media? I believe (I'm not 100% certain) that if you mount drives in /mnt, desktop icons never appear, whereas if in /media they will appear if you've ticked the volumes_visible box in gconf-editor.

So, if that is so, try changing your external drive fstab mountpoints from /media/whatever to /mnt/whatever, and then go to apps > nautilus > desktop in gconf-editor and tick the volumes_visible box. Since CDs, USBs, etc are automounted in /media that ought to work.

**Edit:** in fact I've just tried this with my internal data partitions, and it works nicely and makes my desktop more tidy. The downside is that you'll have to navigate to your external discs via Places > Computer > Filesystem > mnt. Not as elegant as having them show up in the Places menu.

---

### Post by PureLoneWolf on 2009-05-14
Sorry, yes I meant that I used gconf-editor and you are right that I currently mount everything under /media

Knowing this is superb...and thanks for testing it - I will give that a go shortly :)

---

### Post by PureLoneWolf on 2009-05-22
I just wanted to say that this worked perfectly.  All of my permanently connected drives are hidden away and any other drives/ipods/USB sticks/CDs/DVDs etc all mount on the desktop for easy access.

Thankyou very much for that.  It should be noted that anything mounted under your home folder, also displays the volume icons.  I tried to have a /home/me/Shares folder to mount them all in and the volume icons appeared too - So not only under media.

Under /mnt though, everything hidden.

Thanks again

---

