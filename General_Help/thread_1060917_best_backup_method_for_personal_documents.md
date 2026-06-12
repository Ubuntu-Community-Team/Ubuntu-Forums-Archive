---
title: "best backup method for personal documents?"
date: 2009-02-05
forum: General Help
---

### Post by shane2peru on 2009-02-05
Ok, I would like some input here as far as backing up files, not the OS.  I know there are several ways to backup the OS that is not what I'm looking for.  I want a way to backup my documents, pictures, music, all to data DVD's.  The catch is when it is time to backup again, I don't want a lot of repeated stuff.  Also I don't have enough room to duplicate everything at once on my hard-drive.  So, what is recommended for this?  I would like a simple thing that would just go through and figure size for the DVD and burn it to DVD automating it as much as possible.  Any ideas would be much appreciated!  Thanks!


Shane

---

### Post by hyper_ch on 2009-02-05
I'd say rsync

---

### Post by shane2peru on 2009-02-05
> **hyper_ch said:**
> I'd say rsync

Unless I missed something, I don't think it is quite possible to rsync to a DVD to back things up.  I need to be able to backup my files to a DVD or CD, not a hard disk.  If this is possible, please do explain.  Thanks.

Shane

---

### Post by shane2peru on 2009-02-05
I came across multicd it is in the repos and it is what I want, however I really wanted a gui one.  I don't mind cli, but would be great to have this in a gui for others to easily use.  All other suggestions would be greatly appreciated!  Thanks.

Shane

---

### Post by shane2peru on 2009-02-05
ok, after tinkering around with multicd it is not user friendly.  I didn't figure out how to get it working correctly.  It is a real pain.  Any other backup solutions that you know of would be greatly appreciated to backup data across several dvds.

Shane

---

### Post by shane2peru on 2009-02-06
Ok, this is pretty sad that there is no simplified way to back your personal data (documents, folders, Music, Pictures etc.).  After a lot of tinkering with multicd I'm finally backing up my data, however it requires a lot of extra disk space or time, and is not user friendly.  I have to configure multicd to make the backup images (only works in ext2) then mount that image with ```
sudo mount -t ext2 -o loop multicd_image11 /media/multicdimage 
``` and then insert a disk and burn the contents in that folder to a dvd.  I set it to make all the images (about 12) at 4.4GB per image, and am now burning them.  Not a practical solution for backing up your data, very time consuming.  It does take the brain work out of figuring out how much will fit on the dvd or cd or whatever medium you are using.  Really too bad someone couldn't come up with another way of doing this.

Shane

---

### Post by FluffyElmo on 2009-02-06
This article mentions a couple of possibilities. MondoRescue seems to be closest to what you want, it has a character based gui which is at least a small step up from the command line.
[http://www.linux.com/feature/150600](http://www.linux.com/feature/150600)

---

### Post by shane2peru on 2009-02-06
> **FluffyElmo said:**
> This article mentions a couple of possibilities. MondoRescue seems to be closest to what you want, it has a character based gui which is at least a small step up from the command line.
[http://www.linux.com/feature/150600](http://www.linux.com/feature/150600)

Where were you yesterday? ;)  Thanks for the info.  I'm looking into Mondo, and about 1/4 of the way done burning DVD's.  I will definitely look into Mondo though.  I found this thread on using it: [http://ubuntuforums.org/showthread.php?t=75386&highlight=mondo](http://ubuntuforums.org/showthread.php?t=75386&highlight=mondo)

The info may be somewhat outdated, perhaps it will work great in GUI mode now.  Thanks for the info. 

Shane

---

### Post by DGortze380 on 2009-02-06
You can buy an external drive for the price of a stack of DVDs and run rsync with one command, or a script...

If you want DVDs after that, image the backup, split the image, burn...

DVDs will ALWAYS be more time consuming and less convenient, the advantage is a very long term backup... you decide.

---

### Post by shane2peru on 2009-02-06
> **DGortze380 said:**
> You can buy an external drive for the price of a stack of DVDs and run rsync with one command, or a script...

If you want DVDs after that, image the backup, split the image, burn...

DVDs will ALWAYS be more time consuming and less convenient, the advantage is a very long term backup... you decide.

External's have not dropped quite that low in price.  They are dropping, and you do bring a valid point about pricing, however ATM the external hdd is not an option, and I happen to have a mess of DVD's to backup on.  So, hence my current situation.  I had 2 external hdd that I used rsync with, it was great and simple, then my external kicked the bucket, and the second one died a few weeks later.  :(  Is your backup backed up?  :KS

Shane

---

### Post by shane2peru on 2009-02-08
mondo is the way to go if you are wondering, install mondo

```

sudo apt-get install mondo

```

Reboot, I think this is necessary.  Then in the terminal once again:

```

sudo mondoarchive

```

Follow the instructions on the screen!  It is pretty simple over all, and seems to work fairly well.

Hope someone finds this of value.

Shane

---

