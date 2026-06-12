---
title: "Ubuntu delay at 9.04 and emerald themes"
date: 2009-05-04
forum: Desktop Environments
---

### Post by chaoscrum on 2009-05-04
Hello People

I downloaded and installed Ubuntu 9.04.
What i noticed is that maximizing minimazing resizing time is increased about 1.5 seconds.
Also when i maximize and the music plays at the default media player (dont remember the name now,i am in xp) the music stops like the pc overloads. 
Any ideas what might cause that.
In ubuntu 8.10 that issue didnt exist.

I have another question.
I have read that beryl and emerald created compiz fusion . How i use the emerald themes 

Should i download 8.04 ? Are there any difference between 8.04 and 9.04?

Thank you

PS maybe it is wrong section sorry :(

---

### Post by overdrank on 2009-05-04
> **chaoscrum said:**
> Hello People

I downloaded and installed Ubuntu 9.04.
What i noticed is that maximizing minimazing resizing time is increased about 1.5 seconds.
Also when i maximize and the music plays at the default media player (dont remember the name now,i am in xp) the music stops like the pc overloads. 
Any ideas what might cause that.
In ubuntu 8.10 that issue didnt exist.

I have another question.
I have read that beryl and emerald created compiz fusion . How i use the emerald themes 

Should i download 8.04 ? Are there any difference between 8.04 and 9.04?

Thank you

PS maybe it is wrong section sorry :(

Hi and what is the model of the graphics card?
If you would like to know more about emerald you may look at the FAQ's link in my signature.

---

### Post by chaoscrum on 2009-05-04
my pc specs 
core2duo 2.13 ghz
 2g ram
ati 3650 ddr3  512 mb

---

### Post by webdebbyjoss on 2009-05-09
I has the same problem on my ATI Radeon 3600HD

found the solution here

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all)

Works right now with no any glitches.

---

### Post by chaoscrum on 2009-05-09
and how you fixed that problem?

---

### Post by marbot on 2009-05-31
Hi everyone

After installing the newest ATI Driver 8.612 on my Ubuntu 9.04, i ran into this problem too. I had a 2sec delay on maximizing / restoring windows using compiz.

I managed to solve it by installing :

XServer with no backfill functionality
[https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill)

Everythings works fine again now,

My config:

- Ubuntu Jaunty 9.04
- ATI Mobility Radeon HD 3400 Series
- Driver Version 8.612

Hope this helps

Good Luck
marbot

---

