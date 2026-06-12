---
title: "Using &quot;made for KDE&quot; software in gnome"
date: 2009-08-25
forum: Desktop Environments
---

### Post by roystreet on 2009-08-25
Hi,
   Since I'm fairly new still, but enjoying becoming more proficient I have a question that has been lingering in my mind for awhile.  Some software out there states something along the line of "made for KDE"  It simply might just be a part of the name, like kword so that you know it made for KDE.  

My question simple is, can that software be used in gnome? (*Or other desktops for that matter*)  If yes, any limitations in how it works.  Is it only some of the software?

Thanks,
~roystreet

---

### Post by ajgreeny on 2009-08-25
Yes it will work fine.  To install you will have to also install a fair number of other kde applications and lib files in most cases, as your chosen app will no doubt depend on some of them.  If you have plenty of disk space that's no real problem these days.

As an example, a lot of users like to have amarok as music player on their machine in spite of running gnome, and I, for one, always install k3b as my disk burning software as I think it is so much better than brasero. I also like digikam more than f-spot, and tend to use that mostly for photo organisation, and that also brought in konqueror, I think, but it all works very well.  kde apps take a little bit longer to load than gtk (gnome) as lib files have to be loaded first in most cases, but it is only a second or two, so no big problem.

So the moral of this story is - use whatever you prefer. Enjoy the choice!

---

### Post by oldos2er on 2009-08-25
KDE apps work on Gnome, Gnome apps work on KDE. In either case, they may look a little odd because of differences in the way each GUI draws its apps, but functionally they should work with no problems (I run quite a few KDE apps on Gnome).

---

### Post by raffraffraff on 2009-08-26
My only addition to these comments is about the look & feel. If you use KDE applications in Gnome, they will not adhere to the Gnome theme. So if you choose a new theme (eg Darklooks) your KDE applications will still look horrible grey-and-blue. There is no simple way to keep them in sync, as far as I know.

I use Amarok in Gnome. I edited this file and changed the colours:
~/.kde/share/confir/kdeglobals

Now Amarok matches my Gnome apps. I'm using Jaunty, Ubuntu with the Darklooks theme and Amarok 1.4.10. I'll post the kdeglobals if anybody's interested.

---

### Post by oldos2er on 2009-08-26
You can also use the KDE package **systemsettings** in Gnome; it will alter each KDE app.

---

### Post by roystreet on 2009-08-27
Thanks everyone for your input! It is *very* helpful.  It sure helps me to continue my process of **totally** migrating over to Linux.

*If you have anything else to input, I will try to read it
~roystreet

---

### Post by TheNosh on 2009-08-27
if you couldn't use KDE apps in Gnome i would be a KDE user, i need my Opera web browser (it's built with QT, the KDE toolkit)

---

