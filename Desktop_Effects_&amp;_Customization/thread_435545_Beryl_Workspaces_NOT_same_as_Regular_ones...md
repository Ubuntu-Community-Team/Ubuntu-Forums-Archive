---
title: "Beryl Workspaces NOT same as Regular ones.."
date: 2007-05-07
forum: Desktop Effects &amp; Customization
---

### Post by twistedbydesign on 2007-05-07
Ok...i dunno if this is how its suppose to be or what.....but whenever i rotate my Desktop Cube in Beryl, it stays on Workspace 1 (bottom right corner). it just minimizes everything and then if i click on whats minimized it flips back to the original side of the cube.
Is there a way to make it so that when i Rotate to a different side of the cube it actually DOES switch my workplaces.
Also my Cube is has 6 sides..is there any way i can make it have 4?

Basically, to make my life simpler and the Cube more practical, I want a FOUR sided Desktop cube that actually has a seperate Workspace on each side.

any help is greatly appreciated.
thanks!!

P.S.  .if you need me to ellaborate just let me know
thanks again.

---

### Post by Schalken on 2007-05-07
You are correct. Beryl and Compiz have a workspaces (or "viewports") implementation seperate from Metacity's. I find when it fails to replace the workspaces applet with its own, I can fix it by setting the number of workspaces to zero and then increasing to four (or your desired number). At least that works with Gnome Compiz Manager. I haven't had a problem with Beryl.

---

### Post by twistedbydesign on 2007-05-07
I'll try that.
Thanks!

---

### Post by ZodiacfreaK on 2007-05-08
if that doesn't work, then this should.
Go to Beryl Settings Manager->General Options->
Change Horizontal Virtual Size to 4
Change Vertical Virtual Size to 1
Change Number of Desktops to 1

---

### Post by twistedbydesign on 2007-05-08
Ok...the first didnt work (beryl actually crashes if i mess with the existing workspaces too much...so i'll just steer clear lol).
So will try ur advice.
thank you.

---

### Post by twistedbydesign on 2007-05-09
Ok That worked!!
Thank you Very Much

---

### Post by terdon on 2007-05-29
Hi all, I have a similar problem. I think I have workspaces/viewports configured correctly but when I right click on the titlebar of a window I don't have the option to send it to another workspace. 

I seem to recall that with a previous version of beryl I could quite happily send applications to other viewports (sides of the cube).

I currently have:

Horizontal Virtual Size : 4
Vertical Virtual Size     : 1
Number of Desktops   : 1

If I change Number of Desktops to 4, I get the "send window to another workspace" option, but that refers to another cube, not another side of the present cube.

Any ideas?

---

### Post by barney_1 on 2007-06-02
I am also looking for a solution to this problem.  It doesn't bother me so much that there is no "send-to-desktop" or "send-to-viewport" option.  What troubles me the most is that a program running on desktop 2 (read: viewport 2) still shows up in the applications bar of every desktop (viewport).

Is there a setting/tweak to change that?

---

