---
title: "home icon as a folder, possible?"
date: 2007-03-26
forum: Desktop Environments
---

### Post by naseem on 2007-03-26
hy I've a question, is there any way to make the home icon on the desktop behave as a folder, in the sence that i drug a file on i t and it gets moved to home dir (sa if it was a regular folder?

---

### Post by jem7v on 2007-03-26
What desktop environment are you running? i.e., Gnome? KDE?

---

### Post by naseem on 2007-03-26
I'm running gnome, and my home is a partion

---

### Post by ComplexNumber on 2007-03-26
> **naseem said:**
> hy I've a question, is there any way to make the home icon on the desktop behave as a folder, in the sence that i drug a file on i t and it gets moved to home dir (sa if it was a regular folder?
it does behave like that. it works like that for me.  what happens when you drag something onto the icon?

---

### Post by naseem on 2007-03-27
if I drug any files or other folder to the home icon on desktop it does not get cut and paste automatically in home directory, instead nautilus  just open the draghed document. have you tried it that way?
I think it is not implemented in gnome by default unless you hack nautilus in some way, and that's what I want to know

---

### Post by ComplexNumber on 2007-03-27
> **naseem said:**
> if I drug any files or other folder to the home icon on desktop it does not get cut and paste automatically in home directory, instead nautilus  just open the draghed document. have you tried it that way?
I think it is not implemented in gnome by default unless you hack nautilus in some way, and that's what I want to know
i haven't hacked nautilus in any way to get that. its always been like that.

---

### Post by naseem on 2007-03-27
sure? cose I'm not the only one having this problem, if I try for instance to bring a picture in my desktop over the "house" icon of gnome desktop I get this error:

not possible to show /home/my/Desktop/nameofimage.png
position is not a folder

and also I cannot make any folder connection pointing to home folder, since i keep getting that error

---

### Post by ExplodingPickle.org on 2007-03-27
Assuming the home icon GNOME comes with is a .desktop file, you could replace it with a symlink (ln -s ~ ~/Desktop/Home).

---

### Post by ComplexNumber on 2007-03-27
> **naseem said:**
> sure? cose I'm not the only one having this problem, if I try for instance to bring a picture in my desktop over the "house" icon of gnome desktop I get this error:

not possible to show /home/my/Desktop/nameofimage.png
position is not a folder

and also I cannot make any folder connection pointing to home folder, since i keep getting that error
i'm 100% sure.

how did you get your home folder to show up in the first place? when you first install ubuntu, the home folder link is there, but just not visible. it is necessary to go into gconf-editor and make the icon visible.

---

### Post by naseem on 2007-03-27
to get the icon I didn't go to gconf-editor I just go to resorses and drug and drop the home entry in the desktop and it appears there, it is used to open nautilus in home folder but I cannot drug and drop files from there to the home itself.
 the icon correspond in terminal to :/home/myself/Desktop/nautilus-home.desktop
which is not a folder...
so maybe with gconf-editor I can get a folder which is linked to home dir?

> Assuming the home icon GNOME comes with is a .desktop file, you could replace it with a symlink (ln -s ~ ~/Desktop/Home)

this worked well, thanks!

---

### Post by naseem on 2007-03-31
@ComplexNumber   ok today I got what you where telling me, I'm a little slow....
gconf-editor>aps>nauttilus>desktop>home icon visible:lolflag: 
thanks!

---

