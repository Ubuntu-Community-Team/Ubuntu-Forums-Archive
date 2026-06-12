---
title: "[SOLVED] wow.....i broke linux.....(gnome)"
date: 2008-01-25
forum: Desktop Environments
---

### Post by panguin on 2008-01-25
okay, so i was playing around with gnome, trying to get my *gorgeous* 19" 1440x900 monitor to work, (it's like a tv on my desk. i use it to watch movies when i dont feel like burning a dvd), and gnome....broke. It said i had to log out for changes to apply.  so, i did what anyone who thinks they know what they are doing would do, and Ctrl-Alt-Bksp'd myself out.

To borrow a line from Sublime, "That's when things got out of control!"

The laptop turned itself off, and when i turned it back on, it booted my to the command line. and no further than the command line. That's it. 

I'm running a live disk of GG right now, so is there any way for me to recover my files? They are still there, (i guess), and i was going to do fresh install in the next week or two anyway.  so, any ideas?

if you need more info, just tell what you need and how to get it. 

pleaseandthankyou!!

---

### Post by panguin on 2008-01-25
never mind.

i'm kind of retarded. all i had to do was look around in nautilus.

oh.  good thing i'm an honors student, with a major in Computer Science no less.

*wonders what college has actually taught him*

---

### Post by chronic on 2008-01-26
no need to reinstall your problem is easily fixed :lolflag:

type this into the command line

sudo dpkg-reconfigure xserver-xorg

follow the onscreen instructions 

post what gfx card you have first and ill see if i can get this problem sorted for you.

EDIT:if your unsure what driver you need to use then select vesa for now

---

### Post by panguin on 2008-01-27
well, it was a bargain dell, inspiron, so i think the graphics card is intregrated into something else. like, i dont really have one that i know of, per se.

but, i screwed up something with Compiz on 7.04, and didnt unistall before i upgraded, so iwas planning on doing a fresh install anywho.

thanks anywho!

---

