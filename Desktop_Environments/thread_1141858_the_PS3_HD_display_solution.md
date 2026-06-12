---
title: "the PS3 HD display solution"
date: 2009-04-28
forum: Desktop Environments
---

### Post by mistercreamer on 2009-04-28
after speading about a week googling to try to find a common solution to increase the screen resolution on the PS3(Linux 7.10) It finally was clear. all you have to do to change your resolution after you have installed unbuntu is:

sudo chmod a=rwx kboot.conf (where ever you put that file)

then add the line 

video=ps3fb:mode:5

inside of the the location of where your sys looks to find kboot.

I guess the sys determs the resolution before the sys starts to load ubuntu..


I didnt have to change anything else, just added that to my Linux="what ever info you have listed here and add video=ps3fb:mode:5" 

Hint:
using mode 5 kinda turned my screen green, but it was at the right resolution, so you may want to use mode:4.

:P

---

