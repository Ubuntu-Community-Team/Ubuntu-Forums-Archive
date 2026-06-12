---
title: "Video resolution for VNC with no monitor attached in Hardy"
date: 2008-08-06
forum: Desktop Environments
---

### Post by pseudogeek on 2008-08-06
Many people seem to have had a frustrating time getting a sensible screen resolution on a box running Hardy with no monitor attached.  Having experienced the pain myself, I thought I would sign up and share my experience.

The problem with Hardy is that it wants to set up the video adapter and monitor by itself.  If there is no monitor, it defaults to a very basic set-up with a choice of three resolutions from 800x600 down to 400x300 (!)  Most of the advice out there (including the FixVideoResolutionHowto post) is based on pre-Hardy builds which I gather (I'm new to this) made it easier to do manual tweaks to the relevant file /etc/X11/xorg.conf.

Hardy puts only a minimum amount of information in xorg.conf by default, and invoking dpkg-reconfigure xsession-xorg (with or without -plow or -phigh) never gives you any video options in the way most posts on this subject expect.

The way to stop Hardy looking for a monitor is to specify one explicitly in xorg.conf with appropriate timings and modelines.  Maybe I'm thick, but it's taken several days to find out the best way of doing this.  All you need is  displayconfig-gtk, which can be run from the command line with gksu or added (it's called “Screens and Graphics”) to the “Other” menu (why it's not right next to Screen Resolution in System/Preferences is a mystery).  Select your video card first, then choose a generic monitor (appropriate for the one you will connect when necessary) and resolution (1024x768 – you wouldn't want more for VNC, would you?).  The appropriate values are written to xorg.conf, but you then have to re-boot to make it so.

Your old xorg.conf is saved as xorg.conf.1, so if there were bits of that which worked better, you can cut and paste between the two versions.  I found that it worked just as well with the “Configured” Device section from the original file as with the specific (Matrox G400 dual head in my case) one put there by Screens and Graphics, for example.  It appears Nvidia users have fun with this section.

What I found I **didn't** need (in the end):
Option “NoDDC”
Option “NoDDCValue”
Option “UseEDID” “false”
Option “ConnectedMonitor” “CRT,CRT”

You don't need to type in HorizSync and VertRefresh lines into xorg.conf yourself, but if you do, (and only those two lines) you will get “Ubuntu is running in low resolution mode” on startup upon which, clicking Configure takes you to Screens and Resolutions.

Hope this saves someone the time it took me.......

---

### Post by hoogmike on 2008-08-26
Thanks pseudogeek, your solution (displayconfig-gtk) is far easier and more elegant then editing the xorg.conf file as many other forum posts suggest.

---

### Post by pseudogeek on 2008-08-26
> **hoogmike said:**
> Thanks pseudogeek, your solution (displayconfig-gtk) is far easier and more elegant then editing the xorg.conf file as many other forum posts suggest.

Pleasure.

---

### Post by ckraimer on 2008-09-07
This worked for me as well - and it's true about the human race that we are collectively getting smarter because i only banged my head for a half-day before finding this!

Thank you VERY much.

One note - at first I kept missing that it didn't have a video card driver selected in the Graphics Card tab in case anyone else is blind like me. . . .

---

### Post by Tass on 2008-11-02
OK - looks like this is just what I need, although it seems that displayconfig-gtk has been excluded from 8.10.  Any ideas?

---

### Post by pseudogeek on 2008-11-03
Hmm. I haven't upgraded yet, but I guess you can get it with Synaptic.

---

### Post by arnoldus on 2009-08-07
How can I combine this with Jaunty?

---

### Post by pseudogeek on 2009-08-07
> **arnoldus said:**
> How can I combine this with Jaunty?

Sorry, I don't know. The whole scheme broke with Intrepid when they removed displayconfig-gtk, and I haven't upgraded to Jaunty yet.  I reckon I need to set aside a day from previous experience of upgrading.:rolleyes:

I'm still using the conf file I generated with Hardy.

---

### Post by samircz on 2011-05-09
this is the best way to fix the monitor problem 

[http://soerennielsen.dk/mod/VGAdummy/index_en.php](http://soerennielsen.dk/mod/VGAdummy/index_en.php)

im test it with ubuntu 8.10 9.4 9.10  10.04  10.10  :popcorn:

---

### Post by pseudogeek on 2011-05-09
> **samircz said:**
> this is the best way to fix the monitor problem 

[http://soerennielsen.dk/mod/VGAdummy/index_en.php](http://soerennielsen.dk/mod/VGAdummy/index_en.php)

im test it with ubuntu 8.10 9.4 9.10  10.04  10.10  :popcorn:

Thanks for that, but I didn't need it.  Maybe because I always had a monitor attached, even though it wasn't usually turned on.  The whole setup has been dismantled, and that old machine is now a bookend so I can't test.

I guess you still have to tell Ubuntu to use a sensible resolution, though.

PG

---

