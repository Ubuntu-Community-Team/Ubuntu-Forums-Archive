---
title: "Eagle installation"
date: 2007-05-12
forum: Education &amp; Science
---

### Post by Anders J on 2007-05-12
I am a fairly new migrator from Windows. I have plenty of experience running Eagle under Windows and I do have an Eagle win/linux license.

I did install Eagle the begninner-safe way using Synaptic, it loaded the packages and I think that it installed Eagle as it should.

Now, as I type "eagle" to start, Eagle displays a window as expected, prompting me to enter the license identity. So far everything is OK, only that the window is blank (or maybe white characters on white background). So now I am stuck.

Being fairly new here:

1. This is obviously a installation package problem, but is that a ubuntu problem or an Eagle (Cadsoft GmbH) problem? How do I report it?

2. How would I perform a text-based work-around (if possible)?

Computer is a brand new BestNote laptop with Intel Core Duo T2250 CPU, ubuntu 7.04, in this case (installation) feeding onboard screen only at 1280 x 800.

Edited:

After fooling around, I relized that the text was not invisible, only "transparent", meaning that if I placed it over a dark area on the desktop, I can read.

Managed to start eagle using sudo and managed to get through the installation, works as expected, BUT all eagle windows still has this weird transparent behaviour so that underlying windows are "glowing through" and that the brightest colour of any wiondow spot in any specific location takes precedence.

Still the same question, is this an ubuntu problem or am Eagle problem?

---

### Post by slimdog360 on 2007-05-12
did you enable the 'desktop effects'? if you did that could be the cause.

---

### Post by Anders J on 2007-05-12
Nope.

Edit: I realize that there is a kind of transparency in visible but nonactive windows. I did test tyhe desktop effects but after playing around unchecked them. Is there by any chance the case that once enabled i have to do something to get rid of it?

Edit again: That it was possible to disable the effects by clicking "enable" was to weird an idea to strike my mind, but that did the trick, removed the non-wanted effects and I can go on configuring Eagle!

---

### Post by ZooY151 on 2008-01-23
Hey I am having this same problem and I can't seem to get around it.  I don't know how to disable the desktop effects...any help?! thanks

---

### Post by htoerrin on 2008-01-24
The current version of eagle does not work with desktop effects. The bug has been reported, and will hopefully be fixed in the next version. You could try to set the following environment variable before you start eagle:

In the terminal, type:
export XLIB_SKIP_ARGB_VISUALS=1
eagle

This works on my system.

---

### Post by ZooY151 on 2008-02-05
Yep, that worked for me, too.  Thanks!

---

### Post by BlueSun on 2008-04-09
[FONT="Verdana"][SIZE="2"]I just installed Eagle 4.16 on Kubuntu64 7.10 using the Adept Package Manager.  Everything seems to work fine, except the text and icons in the Eagle windows are **tiny**, including all the menus and controls.  I can barely read the menu items.  It seems like a window manager problem.  Any suggestions?[/SIZE][/FONT]

---

### Post by Anders J on 2008-04-10
No idea. But I have found the Eagle support to be very competent and I have had quick and good replies from them.

Try them.

---

