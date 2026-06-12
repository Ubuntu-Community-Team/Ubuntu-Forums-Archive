---
title: "gaming data location"
date: 2010-01-15
forum: Gaming &amp; Leisure
---

### Post by aladinonl on 2010-01-15
Hi, 

I want to separate / and /home . I'd like to know the location of game data (like map and all) which is usually big size. So i can allocate my disk space. 

More specifically, I play urban terror.

---

### Post by dfreer on 2010-01-16
Hmmmm, generally games specifically packaged for debian systems are not installed in /home, it would be in /usr/local/games or some equivelent location. I didn't see Urban Terror available in the standard repositories however, which means it could very well have been installed anywhere, including your /home. 

Static files like preloaded maps would probably be found within the main program directory, whereas files downloaded during gameplay (custom maps and such) would likely be found in a hidden folder located in your user folder (such as /home/dfreer/.urbanterror/maps/).

If you know what package you used to install urban terror, that would be helpful in determining the location of your files. Beyond that, you can use the search function to look for certain keywords, like "urban" or "terror" in your file directories. Some intelligent guessing may also prove useful, check for a hidden user folder and in /usr/local, /usr/local/games, /opt/, /usr/games...

---

