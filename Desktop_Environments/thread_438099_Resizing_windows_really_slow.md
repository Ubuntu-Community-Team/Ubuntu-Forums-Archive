---
title: "Resizing windows really slow"
date: 2007-05-09
forum: Desktop Environments
---

### Post by AndersRiggelsen on 2007-05-09
Hi there (new Linux/Ubuntu user here) :)

I really like how clean and simple the Gnome desktop is that comes with Ubuntu as default, but compared to Windows' speed when handling resizing such Ubuntu seems to respond *really* slow. I'm unable to find out if It's just my computer or if it's the desktop in general.

In windows when I resize my windows, they update instantly and it appears very smooth, but on ubuntu, if you resize your windows with a certain speed the window doesn't seem to update one bit at all leaving a large gray area until it randomly decides to redraw.
Also even though the window doesn't update, how come resizing a window that doesn't seem to redraw itself take almost 100% CPU power?
Is it because the desktops on Linux aren't so close to the kernel as it is on windows or is it just because my Ubuntu is improperly configured?

---

### Post by paulfife on 2007-05-09
The first guess would be that you may not have the proper video drivers installed. Without knowing what you have, I can advise that you check the restricted devices manager to see if there is one available for your card. That may help things. Otherwise post what video card you have and someone can probably offer some advice.

---

### Post by AndersRiggelsen on 2007-05-09
I used the restricted ATI video driver in the beginning but it didn't allow me to run anything 3D so I installed the open source drivers which works flawlessly. Can run many 3D games now also through Wine without a problem.
I talked to a friend who has been using linux for a long time and he sais it's normal that Ubuntu has slow window refreshing when resizing windows.

My laptop specs are:

Intel P4 3 Ghz
512 mb RAM
64mb Radeon 9600

I tested the "lag" with and without Beryl as the window manager and it is worst with Beryl enabled. With Metacity it is still there but less noticeable. Still quite annoying though, it doesn't have the same smooth and fast feel that I've seen in other OS'.

---

### Post by paulfife on 2007-05-10
I have an AMD Athlon 2000+, 512MB RAM,  and a 256MB Radeon 9800 card. I've tried Beryl and it is pretty slow for me, but Metacity is pretty zippy. I even have pretty good results on my work machine, running the OS in a VMWare session. I do notice that some of the methods of refresh are a little different. For example, when resizing a Windows Explorer window the folder view flashes annoyingly on Windows, but the rest of the draw is quick and smooth. In Ubuntu, doing a similar operation doesn't cause any flashing, but it seems to favor doing a complete update over keeping up. Perhaps this is what you are seeing?

Is other stuff, like playing videos, or screensavers refreshing at a reasonable rate?

---

### Post by AndersRiggelsen on 2007-05-10
Windows doesn't seem to give me those flashy redraws.

It isn't flashy in that way on ubuntu, it's refresh rate of the contents of the windows is just really low:
[IMG]http://andos.stiaxies.net/stuff/screenie.jpg[/IMG]
When I resize the windows with Metacity I can see that gray area for a split second before the contents of the window decides to redraw.

---

### Post by garba on 2007-05-10
yes that happens because of the gtk libs being painfully slow

---

### Post by AndersRiggelsen on 2007-05-10
I guess it's common then? 
I hope they improve a lot on it in the future :-/

Is there any settings I can tweak to minimize the effect?

---

### Post by garba on 2007-05-10
yep it's common, try using a lighter gtk engine, that might help some

---

### Post by miceagol on 2007-07-14
> **garba said:**
> yep it's common, try using a lighter gtk engine, that might help some

Could you please give some more details of how to do this, and the implications?

---

