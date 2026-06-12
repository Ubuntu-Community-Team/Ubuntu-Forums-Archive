---
title: "firefox 3.5 color problem"
date: 2009-07-07
forum: Desktop Environments
---

### Post by twinspop on 2009-07-07
[Funky color screenie]("http://imgur.com/PTiN5")

Since using 3.5, beta and now final, the color pallet is wonky. Any ideas where to start? I also tried the official Mozilla release of (32bit) 3.5. Same result. If I download the images and open them in other programs, including Firefox 3.0.11, they look normal. 

9.04 x64
Firefox 3.5 from ppa.launchpad.net/fta/ppa/ubuntu

---

### Post by truethug on 2009-07-07
I had this same problem, I fixed it by turning off firefox 3.5's new color management system.  To do this:


[LIST=1]
[*]type *about:config* in the address bar
[*]locate the boolean gfx.color_management.mode
[*]right click and select modify.  Enter 0 as the new value
[/LIST]
for more information read here: [http://blog.patyuen.com/2009/07/04/firefox-35-and-color-management/](http://blog.patyuen.com/2009/07/04/firefox-35-and-color-management/)

---

### Post by twinspop on 2009-07-08
Rockin! That did the trick, tho I still wonder why the color management is broken. :-/

Thanks!

---

### Post by Berlin01 on 2010-04-24
Big Thanks. This helped. Why is this not the default setting?

---

### Post by bulazs on 2010-09-18
Thank you! I needed this trick too.

---

