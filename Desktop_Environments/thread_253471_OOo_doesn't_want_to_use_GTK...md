---
title: "OOo doesn't want to use GTK.."
date: 2006-09-08
forum: Desktop Environments
---

### Post by Ramses de Norre on 2006-09-08
I attached a screenshot of the current looks of my Open Office.

What I'd like is the gtk look of open office like you've got with a fresh gnome install.. I have no idea how to get rid of this ugly interface, all suggestions are appreciated ;)

---

### Post by skymt on 2006-09-08
Run 'ooffice -help' in a terminal, there's an option to choose a GUI toolkit. Then change whatever launcher you use (most likely the Fluxbox menu) to add that option. I can't give you the exact option at the moment, I'm at a Mac kiosk.

EDIT: I'm back at my wonderful Ubuntu box. Turns out the option isn't in the -help output, it's in the man page. It's "--widgets-set gtk".

---

### Post by Ramses de Norre on 2006-09-08
That changed the colours of the toolbars and the menus a bit but I've still got the ugly icons and fonts..

---

### Post by Ramses de Norre on 2006-09-09
Bump..

---

### Post by hw-tph on 2006-09-09
Try setting the environment variable $OOO_FORCE_DESKTOP, like this:
```
OOO_FORCE_DESKTOP="gnome" ooowriter &
```
Note the OOO are three capital o's - not zeros.

If that works well you might want to put this in your ~/.bashrc to always have it specified:
```
export OOO_FORCE_DESKTOP="gnome"
```
For reference, that ugly interface is OpenOffice's own widget set. You can set $OOO_FORCE_DESKTOP to "none".

Håkan

---

### Post by Ramses de Norre on 2006-09-09
Ow this is so nice, I got it to work by combining both suggestions from this thread!:D 
So I did```
export OOO_FORCE_DESKTOP=gnome
oowriter --widgets-set gtk
```
then I looked a bit around in the tools>options dialog and I got it all perfect.
Thanks for your help ;)

---

### Post by Cable on 2006-09-09
So is there a way to say...get OOo to use the HumanBlue icon set that I'm using?

---

### Post by Ramses de Norre on 2006-09-09
Hmm I can choose out of a few themes but not all my instaled ones.. I guess that themes need to have a set of open office icons and not much of them will have that..

---

