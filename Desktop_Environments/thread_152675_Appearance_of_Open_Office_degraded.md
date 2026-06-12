---
title: "Appearance of Open Office degraded"
date: 2006-03-30
forum: Desktop Environments
---

### Post by stig on 2006-03-30
Hi,
I've been using Open Office (OO) v.1.1.5 which I think came with my initial instal of Ubuntu 5.04. Then I upgraded to Ubuntu 5.10 and it was still OO v.1. I carried on using it but have just installed OO v.2 from the repo. I thought OO 2 would replace my OO 1 but it didn't so I have them both for now.

But the OO2 "looks" old-fashioned, like Windows 95 and is nowhere as attractive as the OO 1. By "looks" I the mean appearance of the fonts in the menus and toolbars etc, and the shape of the boxes. For example, the box on the toolbar that shows the % zoom has very sharp corners whereas my OO1 boxes are smoothed corners.

Has the appearnce of OO been changed in v.2 or is there something I can adjust? I can't find anything in the Customise or Options menus. (And my OO1 still displays as before, so it isn't something to do with the computer settings.)

It would be great if someone can help solve this problem

---

### Post by hw-tph on 2006-03-30
Try launching OpenOffice by typing the following:
**OOO_FORCE_DESKTOP="gnome" oowriter2**

If that does help (it should force OpenOffice to use the GTK2 toolkit for the interface, like all Gnome apps), you can put this in your ~/.bashrc:
**export OOO_FORCE_DESKTOP="gnome"**


Håkan

---

### Post by stig on 2006-03-30
Thanks!

I tried it...

...but unfortunately, no, it gives exactly the same appearance in Open Office.

---

### Post by stig on 2006-03-31
Does anyone else have a suggestion of how to solve the above problem?

I note that Open Office web site says of v.2:

"...easier to install, with a whole new look and feel, matched to the type of computer in use".

Does this "matched to the type of computer in use" have anything to do with it perhaps? I am using a Pentium 2.8 GHz, 512 MB, 80 GB hard disk with a 15 inch TFT monitor at 1024 x 768, refresh rate 74 Hz.

---

### Post by Onomatopoetikon on 2006-03-31
I had a tremendous improvement with fonts in OOO by going to Preferences -> View and toggle of the setting about anti-aliasing. I can't remember if I toggled of the "use system fonts" mark too, but playing with those two options did all the difference for me.

---

### Post by stig on 2006-03-31
In my Options, View, the antialiasing is fixed - I can't remove the tick from it. Changing the other settings either seems to have no effect (e.g. system font) or corrupts the display (e.g. scaling).

---

### Post by Onomatopoetikon on 2006-04-02
Hmm, try increasing the min pixel size to something mad... say 56 pixels or so, that would have the same effect as turning it off, more or less.

---

### Post by engla on 2006-04-02
Make sure you installed openoffice.org2-gnome, otherwise it won't be pretty.

---

### Post by stig on 2006-04-05
[QUOTE=engla]Make sure you installed openoffice.org2-gnome, otherwise it won't be pretty.[/QUOTE]

Great! Thanks engla, this is perfect! What a difference! I knew there had to be something - it had looked so bad. Now the fonts are as they should be, the corners of the boxes are rounded off.:p

I wonder how many other people are using Open Office v.2 with it looking the way mine did? I knew it was wrong becasue v.1 had looked so good. But if others have come straight to v.2 they might not know and just think it is the normal appearance!

---

### Post by Biffy on 2006-06-09
[QUOTE=engla]Make sure you installed openoffice.org2-gnome, otherwise it won't be pretty.[/QUOTE]

Wich command should i start OO with to get it in GTK2? I am using fluxbox. openoffice.org2-gnome is installed.

---

