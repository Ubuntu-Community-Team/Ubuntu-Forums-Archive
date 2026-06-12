---
title: "3d desktop cube?"
date: 2010-12-30
forum: Desktop Environments
---

### Post by gmenfan83 on 2010-12-30
i have compiz installed and have it set to rotating desktop but i see some people have the 3d rotating desktop ...can anyone tell me how this is done...i have played around with my compiz settings and cant seem to get it....thanks

---

### Post by daqron on 2010-12-30
Do you mean [Rotate Cube]("http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm#Enable-Rotate-Cube-Effect")?

---

### Post by gmenfan83 on 2010-12-30
> **daqron said:**
> Do you mean [Rotate Cube]("http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm#Enable-Rotate-Cube-Effect")?
thank you and yes ..i have that part down but i would like it to look like the shere cylinder or cube in the link below and even following the directions i cant get it .....also in the instructions to set desktop to 4 i cant for some reason i can not adjust this and can only remain at one
[http://www.ghacks.net/2009/05/25/enabling-the-cube-in-compiz/](http://www.ghacks.net/2009/05/25/enabling-the-cube-in-compiz/)

---

### Post by daqron on 2010-12-30
That's pretty cool, but I've never seen it work like that, and there are lots of Google hits for the # of desktops being limited to 1 (tried it on my system; same problem). Sorry I can't be more helpful; perhaps a compiz expert is about and can assist.

---

### Post by Frogs Hair on 2010-12-30
Install compiz-plugins-extra and enable 3D windows and cube deformation.

---

### Post by gmenfan83 on 2010-12-30
> **Frogs Hair said:**
> Install compiz-plugins-extra and enable 3D windows and cube deformation.
thanks Frog Hair but that still did not do it ..i have searched everywhere and cant seem to figure this out

---

### Post by daqron on 2010-12-30
> **Frogs Hair said:**
> Install compiz-plugins-extra and enable 3D windows and cube deformation.
Try: ```
sudo apt-get install compiz-fusion-plugins-extra
```
The 3D windows still don't seem to work out of the box, but it does get you closer to the cube you wanted.

---

### Post by gmenfan83 on 2010-12-30
> **daqron said:**
> Try: ```
sudo apt-get install compiz-fusion-plugins-extra
```The 3D windows still don't seem to work out of the box, but it does get you closer to the cube you wanted.
well i have the plug ins installe and everything checkmarkrd properly but still no go ...i think it has to do with my desktop windows i have a lot of them and i think i should only have 4 for the cube

---

### Post by gmenfan83 on 2010-12-30
finally figured it out ...in order to put the cube or sphere in its mode you have to hold ctrl + alt and left click on mousse....it awesome!!!

---

### Post by daqron on 2010-12-30
> **gmenfan83 said:**
> finally figured it out ...in order to put the cube or sphere in its mode you have to hold ctrl + alt and left click on mousse....it awesome!!!
OK yeah that is pretty cool. Glad you posted the solution. I'm going to use this now :) Good work.

---

### Post by Rev3k on 2011-02-28
I downloaded the plug in mentioned above and 3d windows worked, but after a restart they stopped working.  In the compizconfig setting manager, nothing has changed, 3d windows is still checked and all of the detailed settings within 3d windows are the same.  I have looked everywhere for solutions, I fixed all bugs found after running compiz --replace, I have added compiz into startup applications.  I cant find this problem any where, is anyone familiar with it or have an idea of how to fix it?

---

