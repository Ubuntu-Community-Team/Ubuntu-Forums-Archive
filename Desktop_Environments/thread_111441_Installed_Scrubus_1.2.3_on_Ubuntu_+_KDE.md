---
title: "Installed Scrubus 1.2.3 on Ubuntu + KDE"
date: 2006-01-02
forum: Desktop Environments
---

### Post by branco on 2006-01-02
Hi all!

Recently I did a complete reinstall of Breezy from scratch. I like KDE so I installed KDE 3.4.5 from the Kubuntu repos, and then went on to remove GNOME by removing *everything* that has to do with GNOME. Then I reinstalled Kubuntu-desktop package. That in itself could have little to do with this problem, but I thought it was worth noting.

Now, I have installed Scribus from the Scribus repos, and it simply doesn't work.

The repos are these:
 
deb [http://debian.scribus.net/debian/](http://debian.scribus.net/debian/) breezy main restricted 
deb-src [http://debian.scribus.net/debian/](http://debian.scribus.net/debian/) breezy main restricted 

Scribus shows the splash, and says something like "There are no suitable fonts on your system" and exits.

Now, I did install most of the font packages available in the Ubuntu repos including the ms ttf core fonts. I also installed all scribus-related packages (both dependencies and recommended ones) except "scribus-cvs" which I assume is the current unstable version.

What could be the problem here? Has anyone had any success/probs with Scribus repos before?

TIA

Branco

---

### Post by anil_robo on 2006-01-02
As of now, KDE and GNOME do not go well together. I tried installing both together, and many applications crashed remarkably. So I reverted to pure GNOME, and I dread installing a single K-application - not even amaroK! :(

---

### Post by shin on 2006-01-02
A little google and here is the reason.

access("~/.scribus/scribusfont.rc", F_OK) = -1
ENOENT (No such file or directory)

The file $HOME/.scribus/scribusfont.rc should contain
a list of directories that contain Type1 or TTF fonts

Create this file and put there something like:
/usr/share/fonts/truetype
/usr/share/fonts/type1

To get all of your font paths - check /etc/X11/xorg.conf

---

### Post by branco on 2006-01-02
To anil_robo:

Well, this is not to start the GNOME vs KDE flame war. However, I find KDE apps better-looking and KDE in general. The only thing I actually miss from GNOME is the speed (especially when copying large number of files). Actually, up until KDE 3.5 I had both GNOME and KDE on my Ubuntu box and they worked flawlessly together. All KDE apps started a bit slower under GNOME but they all worked normally later on.

To shin:

Thanks big time! It worked. I think I remember not having to do this before tho...

---

