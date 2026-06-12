---
title: "Scroll bar colour - some change, some don't"
date: 2013-02-21
forum: Desktop Environments
---

### Post by grey1beard on 2013-02-21
In an attempt to make the scroll bars more visible on my Gnome 3.2.1 desktop, running ubuntu 12.04, I installed **Ubuntu Tweaks** and  then **Gnome Color Chooser**.

I've managed to change the scroll bars (no overlays) to a colour of my choosing, but it only seems to affect software - *Firefox*, and the programmes in *Applications* that I've looked at so far - but the scroll bars in *Places*, like Home folder, etc., seem to be unaffected.

See attached screenshot, scroll bars on right.

Is this how it is, or is there a method in Gnome Color Chooser that I haven't managed to understand ?
( I found a useful set of definitions in Archlinux.org/ Gnome Color Chooser.)

John

---

### Post by grey1beard on 2013-02-21
Extra info.
I'm using Radiance for the gtk theme, and for the windows theme.

I've read a post of someone editing the  folder *Themes/Ambience/metacity-1* in order to solve a similar, but different, problem of their own, and am wondering if I might find a solution in editing *Radiance/metacity-1* ?

John

---

### Post by Frogs Hair on 2013-02-21
Matacity is the window border and buttons. Look in file system usr/share/themes/radiance/gtk 3/apps/nautilus.

You will have to be root to make changes in the file system if you find what you are looking for. ```
gksudo nautilus
``` 

You can download extra ambiance and radiance themes to experiment with from the link. 
     
[https://launchpad.net/ubuntu/+source/light-themes/0.1.9.1-0ubuntu1.2](https://launchpad.net/ubuntu/+source/light-themes/0.1.9.1-0ubuntu1.2)

---

### Post by grey1beard on 2013-02-22
Thanks, Frogs Hair. That's just the pointer I need.

Regards
John

---

### Post by grey1beard on 2013-03-07
Well I finally got to giving it a try, and followed your lead to get to the relevant .css stylesheet.
But this...
> **Frogs Hair said:**
> ........... if you find what you are looking for. ............
............is the problem.
Not being familiar with the language, I can't see anything in the way of 'scroll bar' which is the only thing I need to change.
Either changing the colour of the scroll bar background, or the 'scroll button'(?) would be fine, so can you tell me what the correct nomenclature is.

Many thanks,
John

---

### Post by grey1beard on 2013-03-07
There is an additional problem, I now realise.
The design of the scroll bar in some of the software is a lozenge shaped button in a round ended 'track' with a small arrow at each end.
However, some of the installed applications use the 'hidden' rectangular button with a narrow track on the edge of the window, and it is this style that I am trying to change.
I can't see any common factor that links one group and differentiates it from the other.

---

### Post by Frogs Hair on 2013-03-08
The link will help to remove the overlay scroll bars and all applications will then have the old scroll bar style. As for the color, I don't know may way around the Gnome  3 CSS .  [http://www.liberiangeek.net/2012/03/disable-ubuntu-overlay-scrollbars-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/03/disable-ubuntu-overlay-scrollbars-in-ubuntu-12-04-precise-pangolin/)

Theme Tutorial: [https://live.gnome.org/GnomeArt/Tutorials/GtkThemes](https://live.gnome.org/GnomeArt/Tutorials/GtkThemes)

---

### Post by grey1beard on 2013-03-11
Thanks for your last post, Frogs Hair. 
I've got around to getting rid of the overlays, and have been experimenting with Gnome color chooser, as the attached pic will show.
While I've found the lack of guidance, like a glossary, a bit of a pain, just by altering colors and 'Apply'-ing the results, I'm starting to get some idea of what it can do.
The differences between the results for Applications and Places is still unpredictable, but I've just had a quick overview of your** Themes Tutorial **link, and I believe the answer lies there.
As most of it goes over my head at present, it will be some time before I learn enough to get the final result, I suspect.

Still, that's the only way to learn, I guess.
Thanks for your help, thus far, and I'll leave this thread unsolved for now, just in case........ :)

John

---

