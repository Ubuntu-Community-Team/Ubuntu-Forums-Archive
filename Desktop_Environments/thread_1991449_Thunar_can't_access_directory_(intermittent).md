---
title: "Thunar can't access directory (intermittent)"
date: 2012-05-30
forum: Desktop Environments
---

### Post by dave0109 on 2012-05-30
I've had this problem come up twice now, once was a few weeks ago when I was still on 11.10 and also just now with 12.04.

The first time, I hooked up my phone and mounted it as an external drive, but one directory didn't show as a directory in Thunar.  Instead there was a grey icon with a small cross, and the name was shown as the full path.  Double clicking on the icon resulted in a "which application to open with" style dialog, saying the the file type was (null).

The second time just now was a directory inside a truecrypt partition.  Same problem.  I fired up the command line and could cd into the directory no problem and listed the contents.  I then remembered that something has installed Nautilus on my machine (which I've not bothered looking into yet), so I fired that up, and it was perfectly fine with the troublesome directory.  Then, some time during the process of hitting refresh and changing the type of icon display, Thunar decided to crash.

Anyone else had similar issues?

---

### Post by rkdwv on 2012-08-04
I had. Right clicked on "null type" file, selected "properties", thunar has crashed, reloaded, and then everything was ok. I consider it's a bug.

---

