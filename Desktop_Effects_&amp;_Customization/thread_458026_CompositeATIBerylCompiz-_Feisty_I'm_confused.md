---
title: "Composite/ATI/Beryl?Compiz- Feisty I'm confused"
date: 2007-05-29
forum: Desktop Effects &amp; Customization
---

### Post by Mtnman71 on 2007-05-29
Ok,

I'm new to Ubuntu yet have to say I like it very much so far.  There is some great information on the forums however when it comes to desktop affects, Compiz, Beryl, ATI, Nvidia, composite extensions, etc.....I'm completely overwhelmed and confused now.  

I used to run Mandriva both gnome and KDE and used beryl with little or no trouble at all.  Sure I had to manually configure /etc/X11/xorg.conf but it worked none the less.  I have to say with Ubuntu its been a chore and to now still unsuccessful.  

I currently scrapped my old load to start over.  I have feisty fawn 7.04 on there now and desktop affects is working.  Does this mean I have compiz loaded?  or is this another feature?  <===Question 1

I am running an ATi Radeon x300.  As I sit now, I can run desktop affects yet my 3d Screen savers do not run too well if at all.  Now to cure that I simply install flgrx drivers.  

I have not done this yet because when I do, I will lose desktop affects.  I've tried Envy to auto load the ati driver and then I have everything with the exception of 3D desktop experience.

Question 3===>  Simply.....Do i need to load my ati driver to get compiz and/or beryl to run?
I'm completely tied like a pretzel right now on which way to go.  Anyone have a simple direct method to get my video card working 100% correctly?  I want all features.  I don't want to move ahead until I can somehow organize each thread to follow.  At this point I’m just too confused.  Some grounding would definitely be appreciated.

thanks,

mtnman71

---

### Post by blazercist on 2007-05-29
Desktop effects is compiz, the reason you lose desktop effects when you install fglrx is because you need to use XGL with fglrx instead of the standard AIGLX that ships with feisty and operates on vesa.

Install fglrx and then follow is link:  [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

---

### Post by Mtnman71 on 2007-05-29
Thanks.  This seems a more straightforward path.  Exactly what I was looking for.   I appreciate the grounding!

mtnman71

---

