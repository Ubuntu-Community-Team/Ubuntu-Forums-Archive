---
title: "Can I access MP3's stored on a Mac?"
date: 2006-08-26
forum: Desktop Environments
---

### Post by greggfathead on 2006-08-26
Hello - I have an old iMac running OSX and holding about 80gb of MP3's that I use as a music server.  Is there any way I can either...

1) access the iTunes library from my Ubuntu laptop using some Linux-based music player or

2) access the MP3 library directly by file sharing from the Mac and just play the MP3's from my Ubuntu laptop, without having to physically move the files onto my Ubuntu box?

Any help would be greatly appreciated - thank you for your time!

---

### Post by reacocard on 2006-08-26
try ourtunes: [http://ourtunes.sourceforge.net/](http://ourtunes.sourceforge.net/)
it's not a music player, but it can search and download shared itunes music. and it's a java app, so you don't even need to install it. just download and run the .jar file. works on windows and OSX too.

I also think banshee can access iTunes shares with it's DAAP plugin.

---

### Post by aysiu on 2006-08-26
```
sudo aptitude update
sudo aptitude install banshee-daap banshee
```

---

### Post by peabody on 2006-08-26
I'd second the banshee recommendation, it can hook up and find iTunes music sharing.

---

### Post by greggfathead on 2006-08-26
> **peabody said:**
> I'd second the banshee recommendation, it can hook up and find iTunes music sharing.

Sweet - got banshee installed and it accesses my iTunes library on my mac perfectly, thank you!  Now I just need to figure out why my sound is not working, but I'll deal with that one at a later date.  Thank you again!

---

