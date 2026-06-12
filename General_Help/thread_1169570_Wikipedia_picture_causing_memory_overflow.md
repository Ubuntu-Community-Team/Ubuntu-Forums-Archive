---
title: "Wikipedia picture causing memory overflow"
date: 2009-05-25
forum: General Help
---

### Post by change_mode on 2009-05-25
The full version of this image

[http://en.wikipedia.org/wiki/File:Sun_and_VY_Canis_Majoris.svg](http://en.wikipedia.org/wiki/File:Sun_and_VY_Canis_Majoris.svg)

causes my system to use up all memory. Can someone confirm the bug? 
Where is the error: Firefox or Ubuntu's image rendering?

---

### Post by whoop on 2009-05-25
I have no problems here.

---

### Post by BUSHYBOB on 2009-05-25
No problems either.

1gig pentium3 250 meg of ram.

I am actually controlling my win98 machine from the above via vnc cos its the only machine that Ican use dialup(spit) on.
1gig processor and 384 meg using firefox 1.5

---

### Post by wannjanjic on 2009-05-25
I have the same problem. After I click on the image, system memory is all used up. I think it is something with firefox and rendering of SVG images.

---

### Post by jojo1224 on 2009-05-25
When I opened it on my acer aspire one running ubuntu 8.10 with openbox and the gnome panel I went from 200MB ram usage to 940MB out of 997MB and my swap usage went up 35% out of my 1GB. BTW im using Firefox 3.0.10.

---

### Post by whoop on 2009-05-25
Are the people having trouble using 32bit by any chance? As I am using 64bit...

---

### Post by whoop on 2009-05-25
Hang on guys, I do have the problem. Not when I visit the link, but when I click on the image. Didn't read the first post close enough...

Added bugreport: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/380318](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/380318)

---

### Post by change_mode on 2009-05-25
> **whoop said:**
> Added bugreport: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/380318](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/380318)

Good, I was just about to do the same :)

---

