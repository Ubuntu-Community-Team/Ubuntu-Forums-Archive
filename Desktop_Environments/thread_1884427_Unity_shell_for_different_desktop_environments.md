---
title: "Unity shell for different desktop environments?"
date: 2011-11-21
forum: Desktop Environments
---

### Post by jimijames on 2011-11-21
So, I've been looking into different desktop environments for a few weeks now, and while I really like the unity interface in ubuntu, I was hoping to implement it in a more lightweight desktop environment (xfce or lxde vs. gnome).

I don't need it to be lightweight because of hardware restrictions.  I just want it that way to speed up boot time and decrease power consumption.

Are there any plans to implement unity on alternative desktop environments?  Am I completely off base thinking that lxde or xfce would be noticeably faster than gnome (with the unity shell)?

I apologize for the beginner question, I've only just begun reading up on this stuff.  I would eventually like to 'graduate' to using arch linux, but that's a long way off yet.

---

### Post by collisionystm on 2011-11-21
> **jimijames said:**
> So, I've been looking into different desktop environments for a few weeks now, and while I really like the unity interface in ubuntu, I was hoping to implement it in a more lightweight desktop environment (xfce or lxde vs. gnome).

I don't need it to be lightweight because of hardware restrictions.  I just want it that way to speed up boot time and decrease power consumption.

Are there any plans to implement unity on alternative desktop environments?  Am I completely off base thinking that lxde or xfce would be noticeably faster than gnome (with the unity shell)?

I apologize for the beginner question, I've only just begun reading up on this stuff.  I would eventually like to 'graduate' to using arch linux, but that's a long way off yet.



The only reason lxde and xfce are faster is because they are not running Unity. Unity depends on gnome.
lxde and xfce uses only pieces of gnome.

your best bet is to just run unity 2D

---

### Post by 3Miro on 2011-11-21
2 components determine the speed of a DE. One is the Windows Manager and the other is the applications that are being used. Unity 3D uses Compiz, which is one of the heaviest WM due to the large number of effects. XFCE has xfwm4 and LXDE has OpenBox, both of which support only minimum effects and provide fast speed.

Then come the applications, for example file managers like Thunar and PCManFM are optimized for speed, while Gnome's Nautilus has more features. When I was using Gnome 2, I would still prefer Thunar over Nautilus because it was snappier. Gnome in general comes with a bunch of daemons that run in the background and use resources (and provide some features that LXDE or XFCE don't have or need more effort to setup).

You can improve the speed of your Unity by using some of the lighter applications, like Parole instead of Banshee and Totem. Removing some of the Gnome daemons, however, can break the system and you will be stuck with Compiz WM no matter what.

---

### Post by jimmydean886-2 on 2011-11-21
Unity 2d works on just about any desktop environment like KDE, LXDE, XFCE, etc. It's just another program. Try pressing alt+f2 and typing:
```
unity-2d-spread
```
Since Unity 2d relies not on WM's, it is also a lot faster when used with a lighter desktop. GNOME and KDE are awfully resource heavy, but the end result (at least to me) is altogether absolutely impressive.

Anyway, give it a try. I'm not sure if all DE's support Alt+F2, so you may have to run it by going into /usr/bin and double-clicking on it so that you don't have a terminal window open every time you go to run it.

Hope this all helps!

--Jimmydean886-2--

---

### Post by jimijames on 2011-11-21
Thank you guys for all of the responses - I was using unity 2d (with gnome however) some after reading the responses, and it does most of what I use unity 3d for.  The search function is the most important for me, in terms of streamlining productivity.

I'm not interested in all of the desktop effects - only in being able to navigate quickly to the program that I need to use.

Thank you again for the help, when I get some free time I'll definitely experiment some more with this.

---

