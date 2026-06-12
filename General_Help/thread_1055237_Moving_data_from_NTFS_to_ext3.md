---
title: "Moving data from NTFS to ext3"
date: 2009-01-30
forum: General Help
---

### Post by Dumain on 2009-01-30
Greetings.

I'm about to give Ubuntu another shot (8.10), however I'm wondering if its possible to somehow format a disk (new one) with ext3 from the Live CD (or Wubi?), and then move data from my NTFS formatted drives to the new ext3 one via Windows?

I've seen using the search that there are apparently some apps for reading "linux-partitions", but can they also write to them? (Also, any indication on (read: experience with) which is best for this and why is greatly appreciated.)

I have imagined it would be something like this:
Format new disk with ext3 from Live CD or something similar (don't know if Wubi can do formatting stuff)
Boot to windows and copy from old NTFS drives using a "special app"
Then format and install Ubuntu on my current OS disk and toss the others (I'm making room for SATA so the ide's have to go).
Then if that works and goes as planned, I'll have my OS disk with: /, /home and swap (those are the 3 basics, yes?), and then the new disk with all my data as for instance '/data'.


(The new disk hasn't arrived yet, so I'm merely "gathering intel" at the moment, so I can be prepared)

---

### Post by bodhi.zazen on 2009-01-30
It is probably easier to do from Ubuntu as Ubuntu recognized both NTFS and ext3

ext4 is here and is available in 9.04 (although 9.04 is in alpha right now).

You can mount ext3 in Windows if your use the windows driver :

[http://www.fs-driver.org/](http://www.fs-driver.org/)

That drive will probably not work with Ext4 ;)

---

### Post by bishounen on 2009-01-30
Here's an even easier solution for you:

1)  Boot your machine with the new drive in it using the Live boot CD.

2)  Format the new drive to ext3 or 4 using the live CD.

3)  Mount both the freshly formatted drive AND your windows drive by "right-click -> Mount" in the "Places" menu.

4)  Copy over the data you wish to preserve by drag-n-drop from one drive to the other.

5)  Once you are certain you've copied over all the data you want, run the installer on the old Win partition, converting it to Ubuntu.

There you go!  No need to install crazy drivers in Windows or even reboot!  Just boot up with the Live CD, and it has the tools to handle all the rest.

Cheers!

---

### Post by Dumain on 2009-01-31
That sounds like a nice solution, thanks.

Am I correct to assume that if I use ext3 I can just upgrade the file system later on when ext4 is available in the package "thingy"?
Unless I understood wrong it's only available with the alpha of 9.04 at the moment?

Being a complete beginner still, I figure that I'm better off with a current release such as 8.10, rather than an alpha?

---

### Post by bishounen on 2009-02-01
> **Dumain said:**
> That sounds like a nice solution, thanks.

Am I correct to assume that if I use ext3 I can just upgrade the file system later on when ext4 is available in the package "thingy"?
Unless I understood wrong it's only available with the alpha of 9.04 at the moment?

Being a complete beginner still, I figure that I'm better off with a current release such as 8.10, rather than an alpha?


Honestly, I don't know if you can upgrade the file system.  However, just reasoning a bit about it I would imagine not.  Seeing as the file system is the foundation of your disk structure, I'd guess that changing the file system without a disk wipe is about as possible as changing the foundation of your home without moving the house.

Again, I'm not 100% certain on that one, perhaps a more experienced Ubuntu Guru can answer that one for you.

And yes, the 9.04 version is the only version ext4 is currently available on by default.  There might be an upgrade or backport for 8.10 though.  You could try going into the "Software Sources" app and on the "Updates" tab, select the "Pre-released Updates" and "Unsupported Updates" checkboxes, click close, and then update the sources list when prompted.

 I'm not really sure what you would need to update or install though.  (Perhaps a newer version of gparted?)  but be aware that even if you format your spare disk with ext4, there is no guarantee that 8.10 will be able to read it.

Frankly, ext3 works really, really well.  No need to upgrade to ext4 unless you have a need to use some of it's unique features.

Good luck!

---

### Post by Dumain on 2009-02-02
> **bishounen said:**
> Honestly, I don't know if you can upgrade the file system.  However, just reasoning a bit about it I would imagine not.  Seeing as the file system is the foundation of your disk structure, I'd guess that changing the file system without a disk wipe is about as possible as changing the foundation of your home without moving the house.
The reason I was wondering is that in comparison, I recall that for instance it's possible to upgrade/update (whatever fits) Fat32 to NTFS in Windows.

> Frankly, ext3 works really, really well.  No need to upgrade to ext4 unless you have a need to use some of it's unique features.
This is true, it's basically the "why fix something that doesn't need fixing"-saying, however without being certain of what the big differences are (I'm not into all the doodad-stuff...yet), I've heard mention of that ext4 is faster than ext3, which on its own makes it slightly more attractive. I don't know how noticable it is though.

> Good luck!
Thanks.

---

### Post by redilyn on 2009-02-02
[COLOR="Red"]Nevermind, Upon further reading you probably do not want to follow my suggestio[/COLOR]n.
__________________________________________________________________________________


You can convert ext3 to ext4 later on but any of the files that were created before the conversion will not have all the benefits of ext4.

I would suggest using a jaunty livecd if possible and format as ext4. You can then use the intrepid livecd to install ubuntu.

After setup, download and install the necessary packages to read/write ext4 and you will be set.

I would love to just suggest jaunty completely but its not ready yet....

---

### Post by jerome1232 on 2009-02-02
> **redilyn said:**
> [COLOR="Red"]Nevermind, Upon further reading you probably do not want to follow my suggestio[/COLOR]n.
__________________________________________________________________________________


You can convert ext3 to ext4 later on but any of the files that were created before the conversion will not have all the benefits of ext4.

I would suggest using a jaunty livecd if possible and format as ext4. You can then use the intrepid livecd to install ubuntu.

After setup, download and install the necessary packages to read/write ext4 and you will be set.

I would love to just suggest jaunty completely but its not ready yet....

Except Intrepid can't use an ext4 file system. So how would you install it. :)

---

### Post by redilyn on 2009-02-02
I trust you caught the part in red right? :)

I know, I actually thought he was going to install to the windows drive.

My / partition is ext4dev in intrepid, but I wasn't sure if he would be able to read ext4 stable in intrepid.

Then again, is there a januty livecd yet??

i'm just going to go over here for a bit...ya thats it...pretend i wasn't even here :)

---

### Post by jerome1232 on 2009-02-02
And you think I'd read the part in red lol! My bad missed it.

---

### Post by Dumain on 2009-02-02
I'll stick to ext3 at the very least until Jaunty is released then I reckon. I'm not gonna dive into experimenting before I've even got my system up and running.

One thing though, I guess it may not work with system-resources etc (stuff you need to boot and such), but if I later convert a partition to ext4, couldn't I just make a new copy of the data on said disk to get the benefits of the new fs or am I way off with that one?

Edit:
And to clarify, yes, I am installing it to the one thats currently holding Windows (fresh reformat inc).

Edit 2:
The below link answered my question about copying for the new features, thanks.

---

### Post by redilyn on 2009-02-02
Have a read, I think this will answer your questions

[http://ubuntuforums.org/showthread.php?t=973701](http://ubuntuforums.org/showthread.php?t=973701)

---

