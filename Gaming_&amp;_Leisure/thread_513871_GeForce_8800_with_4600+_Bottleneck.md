---
title: "GeForce 8800 with 4600+ Bottleneck?"
date: 2007-07-31
forum: Gaming &amp; Leisure
---

### Post by Sockerdrickan on 2007-07-31
Hi these are CPU usage screenshots after INTENSE sessions of the games:

DOOM 3: [http://img401.imageshack.us/img401/5...puusageae4.png](http://img401.imageshack.us/img401/5...puusageae4.png)

Quake 4: [http://img225.imageshack.us/img225/7...puusagejq5.png](http://img225.imageshack.us/img225/7...puusagejq5.png)
Both sessions were rendering of the complete map and not a single room.

Is it the CPU that is bottlenecking it?

---

### Post by Toet on 2007-07-31
Can't open your links here.

---

### Post by Motoxrdude on 2007-07-31
A thing i noticed with linux is that your cpu usage is going to be maxed when playing games with opengl.
As for bottlenecking? Why yes it is but it's not severe. That processor can play those games with ease.

Ps-borken links.

---

### Post by Sockerdrickan on 2007-07-31
Okay maybe I'll buy a Phenom this christmas

---

### Post by Sindwiller on 2007-07-31
Don't use imageshack ffs - use [http://xs.to](http://xs.to) instead!

---

### Post by smartbei on 2007-07-31
Here is an interesting thing I noticed:
When I am using Metacity (the default gnome window manager) or Xfwm (the default Xfce window manager) when I am moving a window around fast the cpu usage gets very high (dual core system, one core at 100%). When I switch to Beryl though, even with all the effects, wiggly windows etc. The cpu stays at 0%!

It was not always like this though. The 1.x versions of Beryl styll used up my cpu - since 2.x though it's been working (probably) as it should.

Can anynone explain this?

---

### Post by brnz on 2007-07-31
The short answer is yes any AMD X2 proc is going to be a bottleneck for that vid card.

BUT - How serious is it as a bottleneck? Really its negligible with the games that are out. I've noticed with Linux I've had to tune down a setting here and there - but I think thats the fault of the environment.. not necessarily the hardware or Linux.

---

### Post by Extreme Coder on 2007-07-31
This article might explain it:
[http://www.phoronix.com/scan.php?page=article&item=781&num=1](http://www.phoronix.com/scan.php?page=article&item=781&num=1)

---

### Post by Motoxrdude on 2007-08-01
> **smartbei said:**
> Here is an interesting thing I noticed:
When I am using Metacity (the default gnome window manager) or Xfwm (the default Xfce window manager) when I am moving a window around fast the cpu usage gets very high (dual core system, one core at 100%). When I switch to Beryl though, even with all the effects, wiggly windows etc. The cpu stays at 0%!

It was not always like this though. The 1.x versions of Beryl styll used up my cpu - since 2.x though it's been working (probably) as it should.

Can anynone explain this?

Yeah, xgl and aiglx makes your desktop a 3-d environment so it gets rendered with your video card vs. your cpu. in a nut shell...

---

