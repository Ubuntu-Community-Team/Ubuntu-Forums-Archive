---
title: "DVD Backups In Linux"
date: 2009-03-02
forum: General Help
---

### Post by s1mp13m4n on 2009-03-02
Hello everyone.  I would like to know how to make legal DVD backups of DVD's I own using Linux.  In Windows I use DVD Shrink, DVD Decrypter, and DVD Fab to do this.  What is a similar software choice for Linux?  Thank you for the help.  :)

---

### Post by RedSingularity on 2009-03-02
You mean you want to make a .ISO file of the DVD?

---

### Post by s1mp13m4n on 2009-03-02
yes, I want to make an .iso of a DVD that I can burn to a 4.7GB DVD-R.  DVDFab will allow you to take a DVD-9 disc and compress it to fit on a DVD-5 disc.  DVD Shrink will allow you to do the same.

---

### Post by lensman3 on 2009-03-02
Look at "vanred". Works like a charm. Google it.

---

### Post by oldos2er on 2009-03-02
k9copy

---

### Post by handy on 2009-03-03
I use DVDShrink, & SmartRipper, they both install very easily under Wine & work perfectly as well as they do under windows.

---

### Post by s1mp13m4n on 2009-03-03
Thank you for the help.  I have never used Wine before, I am new to Linux....and I am loving Linux by the way.  My goal is to not use Windows at all. I have DVD Shrink and DVD Decrypter installed using Wine.  It just installed like it would have in Windows and simply worked.  I wonder what else I can use Wine for?

---

### Post by ene_dene on 2009-03-03
> **s1mp13m4n said:**
> Thank you for the help.  I have never used Wine before, I am new to Linux....and I am loving Linux by the way.  My goal is to not use Windows at all. I have DVD Shrink and DVD Decrypter installed using Wine.  It just installed like it would have in Windows and simply worked.  I wonder what else I can use Wine for?
In my experience many small programs work without any trouble. As for larger programs, I did had some troubles, but usually there exists a solution on wine site. But in time, if you stick to Ubuntu, you'll see that your need for windows programs will shrink, there are a lot of really great programs for ubuntu.
As for copying DVDs Brasero does a wonderful job. You should install the newest version from deb file from [http://www.getdeb.net/](http://www.getdeb.net/) because there are few bugs in the default version (just type: brasero to search and download deb file (same as exe in windows) ). I'm not sure if there is an option to shrink 8Gb DVD to 4Gb, but for that you have dvdshrink, no need to change it if it works fine (it's a great program).

---

### Post by Slim Odds on 2009-03-03
> **ene_dene said:**
> In my experience many small programs work without any trouble. As for larger programs, I did had some troubles, but usually there exists a solution on wine site.


It's not the size of the problem, but what it does and how it does it.

> As for copying DVDs Brasero does a wonderful job. You should install the newest version from deb file from [http://www.getdeb.net/](http://www.getdeb.net/) because there are few bugs in the default version...I would highly recommend **not doing that**. Once you start mixing some .debs that are not in the Ubuntu repositories, you're just asking for trouble.

P.S. I'm specifically talking about applications that Ubuntu provides.

---

### Post by ene_dene on 2009-03-03
> **Slim Odds said:**
> It's not the size of the problem, but what it does and how it does it.
I believe that size is not directly the problem, in larger programs there are probably more things that could get wrong.

> **Slim Odds said:**
> I would highly recommend **not doing that**. Once you start mixing some .debs that are not in the Ubuntu repositories, you're just asking for trouble.

P.S. I'm specifically talking about applications that Ubuntu provides.
I have brasero installed from getdeb on 5 computers and there are no problems. Default version of program is unusable, it detects a blank CD when trying to copy DVD/CD or when trying to do audio CD from mp3. Bug reports exist on this issue. 
I believe that in general it's not wise, but burning CD is basic desktop operation and it has to be done in some way. In my experience there are no problems whatsoever.

---

### Post by mb_webguy on 2009-03-04
dvd95 is another tool similar to DVD Shrink, and it's a Gnome application unlike k9copy.

And if you want something to rip the movies to files playable on your computer or other media devices, you should take a look at Handbrake, dvd::rip, or OGMrip.

---

### Post by 3rdalbum on 2009-03-04
People: Before replying, please note that the OP wants to copy *dual-layer video* DVDs to single-layer discs. Brasero cannot do that yet.

I would suggest K9copy, it's a native Linux program and it's pretty good. Just make sure you get the latest version from [www.getdeb.net](www.getdeb.net) as it fixes a silly little bug that's in the Ubuntu Intrepid version of K9copy. It will pull in a few KDE dependencies too; don't worry, that's perfectly normal and acceptable.

---

### Post by Alchera on 2009-03-05
> **3rdalbum said:**
> People: Before replying, please note that the OP wants to copy *dual-layer video* DVDs to single-layer discs. Brasero cannot do that yet.

Installing DVDFab via Wine and then cloning the dual layer DVD allows that cloned image to be burnt onto another (blank) dual layer DVD.

I am (currently) unaware of any *nix program that can achieve this.

---

### Post by mb_webguy on 2009-03-05
> **Alchera said:**
> Installing DVDFab via Wine and then cloning the dual layer DVD allows that cloned image to be burnt onto another (blank) dual layer DVD.

I am (currently) unaware of any *nix program that can achieve this.
How is that different than making an iso of a dual-layer DVD, then burning that iso to a DVD+/-RW DL -- or, if you have two drives, copying the dual-layer DVD directly?  Because *every* decent *nix burning program can do that.

And if you're talking about taking a dual-layer DVD and backing it up onto a *single*-layer disc, that's what dvd95 and k9copy are for.

---

### Post by mc4man on 2009-03-05
> How is that different than making an iso of a dual-layer DVD, then burning that iso to a DVD+/-RW DL -- or, if you have two drives, copying the dual-layer DVD directly? Because every decent *nix burning program can do that.

if the .iso is copied (dumped) directly off of the disc and has css encryption that's not removed while creating the .iso then if it's burned back to dvd media it will not play to varying degrees. (it will either not play at all or will playback scrambled.

on the other hand an encrypted .iso will playback perfectly when on the hdd

---

### Post by DagMan on 2009-03-05
seems like in that case you could just use dd from the original disk to a file, then from the file to the new disk.  Never tried that with DVD drives though, might have a problem writing to them.

---

### Post by SuperSonic4 on 2009-03-05
> **oldos2er said:**
> k9copy

+1. I've also heard good things about handbrake

---

### Post by mb_webguy on 2009-03-05
> **mc4man said:**
> if the .iso is copied (dumped) directly off of the disc and has css encryption that's not removed while creating the .iso then if it's burned back to dvd media it will not play to varying degrees. (it will either not play at all or will playback scrambled.

on the other hand an encrypted .iso will playback perfectly when on the hdd

I've never had a problem with it, and I've backed-up quite a few DVDs over the years, some of which surely had some sort of encryption.

And as far as that's concerned, since dd makes a bit-for-bit copy of a drive, a DVD burned from an iso made with dd should be essentially identical to the original.  While I haven't looked into it,  I'd think that most Linux disc burning utilities would use dd to make a disc image, since it's such a basic and common command.

---

### Post by mc4man on 2009-03-06
While you may get playback on a pc of *burned, css encrypted media* with some players (totem-xine is particularly good), I think it's generally a poor idea. Playability is certainly not a sure thing.
 
As far as standalone's or licensed software players it's guaranteed they won't.

> a DVD burned from an iso made with dd should be essentially identical to the original.
While your making a bit for bit copy, consumer burners and media can't write to the area where the css info is stored.

---

