---
title: "Desktop panel orientation"
date: 2008-02-13
forum: Desktop Effects &amp; Customization
---

### Post by PasiM on 2008-02-13
I have small but annoying problem with Ubuntu 6.06.

There's 2 panels on desktop, one which contains those applications, places and system menus, normally at top of screen (let's call this one A) and then that another one, normally at bottom of screen (B).

I've moved both panels to bottom of screen so that B is above A. Every time I login, both panels are at bottom of screen but always so that A is above B. I always have to change orientation of A back to top and then back to bottom, to make it go under B. It doesn't take long, but it's a bit annoying to do it every time.

Is there any way to make Ubuntu to remember not only orientation of panels, but also their respective order?

---

### Post by Tenken on 2008-02-13
Try right-clicking panel A going to Properties and setting orientation to "Bottom" and setting the orientation of panel B to "Top"

---

### Post by notwen on 2008-02-14
Perhaps you could also try saving your session.  After you have arranged your panels the way you like them, go to System--->Preferences--->Sessions  I believe the third tab on your Session window will be Current Session and there should be a button to save your current session.  Reboot and see if your panels remain where they are.  I can't recall if Dapper had this option or not, but I know I used it a lot from Edgy on.  Hope this helps. =]

---

### Post by PasiM on 2008-02-19
Tenken: Wouldn't that cause B to be in top of screen? :-)  I want both panels to be at bottom of screen, but in particular order.

This is how I would like panels to be:
[http://img143.imageshack.us/img143/746/image1zy8.jpg](http://img143.imageshack.us/img143/746/image1zy8.jpg)
This is how they are after every login:
[http://img215.imageshack.us/img215/312/image2pg7.jpg](http://img215.imageshack.us/img215/312/image2pg7.jpg)

Notwen: Tried that, no luck, thanks for suggestion anyway.

I found solution to this actually, in case someone else have same problem:

After login, instead of moving panels, I used "Add to panel..." to move all items from panel A (menubar, clock, quit button) to panel B and vice versa. Pretty simple in retrospect :-) but still think that's a bug in Ubuntu, panel order should be saved with user settings also, not only orientation.

---

