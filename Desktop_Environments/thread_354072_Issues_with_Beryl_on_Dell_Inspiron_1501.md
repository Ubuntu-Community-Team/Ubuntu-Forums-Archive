---
title: "Issues with Beryl on Dell Inspiron 1501"
date: 2007-02-05
forum: Desktop Environments
---

### Post by jmc1 on 2007-02-05
I've been working on getting Ubuntu running on my Dell Inspiron 1501 and I've run into some issues getting Beryl working:

First I followed [this guide]("http://lhansen.blogspot.com/search/label/Ubuntu") to get it working. I did all the steps but when I loaded the session there was multicolored static, and I could not get Beryl to take over and it crashed a couple times as well.

Then I went to [this guide]("http://ubuntu1501.blogspot.com/2007/01/beryl-with-xgl-on-ubuntu-610.html") and re-ran the steps after the downloading parts figuring that I had all the stuff anyways, since it was the same files the first guide told me to get. No improvements whatsoever.

Finally, I downloaded the ati driver listed on [this site]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") and ran the script, installing the driver. Now the multicolored static is gone, but I still have no Beryl and the video's acting screwy now, don't know what to call it but there's a diagonal wipe effect going on when I load up a simple folder or load the session.

When I load up the default session (no XGL) everything but Beryl runs fine. Beryl doesn't crash, it just doesn't do anything to the windows or anything.

I'm trying to provide as much info as I can and I would really appreciate any help here.

System Specs that might help:
AMD Mobile Sempron 3500+ (running 32-bit Ubuntu, can switch to 64-bit if it doesn't impact compatibility)
ATI Mobile Radeon Express 1150 (or something like that, number's right though)

The resolution has always stayed fixed at 1280x800 which is where I want it at.

I could really use the help here. I'll wipe Ubuntu and start over if I have to but that means fixing the WiFi again which will take hours using my dialup connection, and I'd rather not go through that. Thanks for any help you guys can provide!

---

### Post by dashnak on 2007-02-05
I'm having problems as well, I used this guide:
[http://ubuntu1501.blogspot.com/2007/01/beryl-with-xgl-on-ubuntu-610.html](http://ubuntu1501.blogspot.com/2007/01/beryl-with-xgl-on-ubuntu-610.html)
And it installed fine, I ran beryl, and I wept in awe at the beauty of it all....
Then I tried to run it again, and my 1501 froze....
And it kept happening on and off.....
Eventually I discovered that if I reinstalled the apps mentioned in the guide, it would work for one boot, and the I would have to reinstall again....
Now, after trying some other configs found in 2 different guides, it simply doesn't work.... beryl-manager loads, crashes, and reverts back to metacity....
Also, even when it was working with the first guide, gnome-settings-daemon never loaded even though it was in my startup programs, I had to do it manually...
Seem buying this laptop wasn't such a good idea after all, although everything else works great...
Any thoughts on this?

---

### Post by shareMenaPeace on 2007-02-05
Today i reinstalled beryl (was not able to use user login)
Do you guys use the default settings, some settings can crash a computer...

Reinstall beryl.
[http://ubuntuforums.org/showthread.php?t=354228](http://ubuntuforums.org/showthread.php?t=354228)

---

### Post by jmc1 on 2007-02-06
Ok. I'll give it a shot now...

---

### Post by jmc1 on 2007-02-06
It's not an issue with Beryl I don't think. I reinstalled it using your guide to be sure, and the thing that's screwing the computer up is the video card. I've ran Beryl in the terminal and it ran the compatibility test and after confirming that everything was compatible, it came up with a "deadly error 11" and could not switch to the Beryl window manager. I don't know if you can call that a crash because everything else I could access worked fine.

---

