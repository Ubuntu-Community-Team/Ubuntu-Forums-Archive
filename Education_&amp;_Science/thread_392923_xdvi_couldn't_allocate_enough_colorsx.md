---
title: "xdvi couldn't allocate enough colorsx"
date: 2007-03-25
forum: Education &amp; Science
---

### Post by xadder on 2007-03-25
After switching from tetex to texlive, I now get the following warning from xdvi:

Couldn't allocate enough colors - expect low data quality

I can click ok and the message disappears, but it is annoying to have to do that every time. I am running  a fairly new Thinkpad T43 with Ubuntu edgy, so there shouldn't be any problems with colour allocation. 

Does anyone know how to remove this annoying messsage?

---

### Post by xadder on 2007-03-29
Anyone?

---

### Post by kleeman on 2007-03-29
Hmm interesting problem. I have the solution (after reading the whole error message :lolflag: ):
Add the -thorough flag after xdvi.

xdvi -thorough

---

### Post by xadder on 2007-03-30
Many thanks! Worked :) 

I wonder if this is something to do with my having Xubuntu installed rather than ubuntu. On my pure ubuntu PC at work I don't get this problem. Anyway, I'll just make a nice alias to take care of this in future.

---

### Post by kleeman on 2007-03-30
I have a full Ubuntu and am getting this as well so I doubt it is Xubuntu causing the problem. My suspicion is that it has something to do with texlive. I only had the problem following the switch from tetex to texlive.

---

