---
title: "Extra Hardrive for videos"
date: 2009-05-17
forum: General Help
---

### Post by kempy1000 on 2009-05-17
Hi

I have just set up my new system using mythbuntu 8.10 amd64.
I let it auto use the enitre 120GB main harddrive in the computer for the system.

However i also have a 320GB hard drive inside that i wanted to use for storing videos and nothing else (no unconverted recordings, no music etc)

I thought of two options after formatting:
1) mount it at the point /var/lib/mythtv/videos/
2) mount it somewere else and make a symbolic link to it.

Are the any better options for this?
I want to keep the 120GB drive for live tv etc

Thanks
Chris

---

### Post by mb_webguy on 2009-05-17
There's no "best" or even "better" place to mount this partition.  It really depends on where you feel it would work best for you.

Personally, I'd mount it as something like /mnt/videos, and then create symlinks to it wherever I needed them, such as ~/Videos or /var/lib/mythtv/videos/.  But this is just personal preference.  You could mount it as ~/Videos, and put a symlink in the mythtv directory, or vice versa.

---

