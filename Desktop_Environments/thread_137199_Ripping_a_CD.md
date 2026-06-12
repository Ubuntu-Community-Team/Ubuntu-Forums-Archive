---
title: "Ripping a CD"
date: 2006-02-27
forum: Desktop Environments
---

### Post by CarlosinFL on 2006-02-27
OK - I usually use WMP to do this but now I am 100% Linux and need some assistance. I purchased a new audio CD from Best Buy & I always take the CD and rip all the songs from the disk to my music/file server as the highest quality .mp3's. Can someone please explain how I can rip music from a CD in Linux? 

*All the CD's I rip are 100 legal and purchased as I am a musician and don't support piracy. I just love taking music on my MP3 player or burn to CD and take with me and leave the master copy safe in its case.*

Thanks for any info!

---

### Post by KingBahamut on 2006-02-27
Youll need to install LAME or some other related mp3 codec. 

Then you can use GnomeBaker to create all the CD to MP3s you want.

---

### Post by jimbren on 2006-02-27
If you want to burn your cds as mp3s, you'll need to have the right codecs installed in order to encode as mp3s.  I can't remember the packages right now since I'm not in front of that machine.  The Easiest thing to do would probably be to install EasyBreezy, which will do all the work for you, including installing a few ripping programs. 

I personally use CDRipper, which I think is a standard part of the distro.  

If you're not running Breezy, or if you run into problems with it, check out the [Ubuntu 5.04 starter guide]("http://www.ubuntuguide.org/").  It is, of course, specific to Warty, but the information is still helpful and it will give you a good starting point for installing the appropriate packages.

Have fun.

jim

---

### Post by CarlosinFL on 2006-02-27
So I need to install "lame"?

```
sudo apt-get install lame
```

---

### Post by KingBahamut on 2006-02-27
Try our Breezy Guide 

[http://doc.gwos.org](http://doc.gwos.org)

---

### Post by aysiu on 2006-02-27
You do have to install the aforementioned codecs first, but for rippping to MP3, Goobox is nice and simple.

```
sudo apt-get update
sudo apt-get install goobox
```

---

