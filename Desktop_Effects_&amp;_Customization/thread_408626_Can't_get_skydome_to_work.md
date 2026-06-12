---
title: "Can't get skydome to work??"
date: 2007-04-13
forum: Desktop Effects &amp; Customization
---

### Post by ruibuntu on 2007-04-13
I have been using beryl for a while now and i had never get the skydome to work. After enabling it and choosing  a picture, it just shows a plain, solid color.



Any suggestions??:confused:

---

### Post by xopher on 2007-04-13
Make sure you're not using images (too large) your 3dcard can't handle.

And here are some 'requirements' for the images I found on the Beryl Forums:

> both dimensions have to be one of these sizes:
2
4
8
16
32
64
128
256
512
1024
2048
4096
8192
etc.
has to fit the formula 2^n with an integer n

---

### Post by reclusivemonkey on 2007-04-13
Some skydome pics that should work;

[http://wiki.beryl-project.org/wiki/Skydomes](http://wiki.beryl-project.org/wiki/Skydomes)

---

### Post by OK3n on 2007-04-14
Image has to be in [COLOR="Red"].PNG[/COLOR].

Sometimes, you have to : select your picture in skydome, look @ skydome, *if it doesn't work*, reload your picture in settings, and it should work.

---

### Post by xopher on 2007-04-14
Actually JPEG's work just as well nowadays, just make sure you have the the support enabled in Beryl-Manager -> Image Format -> [x] JPEG

---

### Post by ruibuntu on 2007-04-14
I can only try Monday but thnx anyway!!

---

### Post by ruibuntu on 2007-04-16
Still showing only some colors but not the picture!!

I tried with differents formats.

---

### Post by dunomous on 2007-05-02
I am having this exact same problem.

 .  I've tried using different file types

 .  I've made sure each file is of appropriate sizes

 .  I've used some skydome images from the suggest link above

 .  I've tried putting quotes around the file path in the beryl setting

I've yet to try:

 .  Restarting Beryl

 .  Restarting X or my session in general

---

### Post by reclusivemonkey on 2007-05-02
Try this one; it works for me.

---

### Post by dunomous on 2007-05-02
Odd, by changing the image to an incorrect file size, turning off skydome, changing it back to a correct 2:1 (2048x1024) and turning skydome back on it worked. Why? I have no idea. Most likely because my prior image size was still a 4:1 and thus too big.

---

### Post by couzin2000 on 2007-05-04
> **reclusivemonkey said:**
> Try this one; it works for me.

I have something odd, here: I downloaded your pic, and it's the only one that works for me.

I tried downloaded some Skydomes from Beryl-look.org, and I get a bunch of pics that look good, but don't work as skydomes. 
So I tried converting them, used Gimp to find out if there was anything I could see that was different from one pic to the next - but size, resolution, color depth, scale ratio, file type, all of it is the same. The only thing I can think of is the compression level of the .png file, but I can't seem to find out from Gimp what it is.

I'll admit your Skydome looks nice, but I need something different -- I want to make sure that the pics I have can be made to work. So I need to have the exact settings so I can save them in Gimp. That way, I can simply use the preset to create the next images.

I just want that to work properly because all the screenshots have me salivating for more!

---

### Post by adhansen5 on 2007-05-09
I am having a tough time getting my skydomes to work.  I recently installed ubuntu 7.04 on my gateway laptop and then added beryl.  Ive used many different "skydome" pics but to no avail.  I also noticed that even when dont have a picture, there is no gradient colors either.  All i see is black, black, black.  My max XvImage size is: 1980 X 1088.  Any help would be greatly appreciated.  

Two other annoying problems:

1.  Integrated Broadcom bcm4306 Wireless b/g is not working
2.  No sound whatsoever

---

### Post by yuku-aki on 2007-10-08
Look up photos that are [equirectangular projections]("en.wikipedia.org/wiki/Plate_carrée_projection"); many people have sites full of skydome pics or pics appropriate to stretch to skydome dimensions.  Mine only accepts 1024x512 (it's a Toshiba Satellite M115); It doesn't look the best, but it works well with already-fuzzy pics like those with fog or mist in them, or super close-up panoramics.

---

### Post by yuku-aki on 2007-10-08
As for the wifi not working - try installing different network managers, and/or wireless managers for both Gnome and KDE.  (I run KDE programs in Gnome with no problem, usually)  And check your hardware profile to make sure it's even recognizing the wifi card or device.  Network-admin and kwifimanager are good 

The sound is a trickier thing - changing drivers may work; once mine was mysteriously silent for weeks until I found that when I put volume control on my top panel, and right-clicked it, I got a whole new volume menu for playback and recording that wasn't in System->Preferences->Sound  (Where one would expect it to be....).  And all the levels had been turned down to zero.  Strange, huh?  

Might as well give them a try.

---

### Post by Linicks on 2007-10-08
I have done some skydomes that work OK for me on 1280x800.  These are 2048x512 in size:

[http://www.nick.ukfsn.org/skydome/](http://www.nick.ukfsn.org/skydome/)

Nick

---

