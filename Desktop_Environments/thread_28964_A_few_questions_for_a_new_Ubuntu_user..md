---
title: "A few questions for a new Ubuntu user."
date: 2005-04-22
forum: Desktop Environments
---

### Post by BAshworth on 2005-04-22
I installed Ubuntu a couple of days ago, and I got most of the major configuration issues worked out.  However, there are a couple that I'm a bit stuck on.

This computer is going to be used by my wife, daughter, and myself, so I have three separate accounts setup on the machine.

1) Is there a way to have installed themes, and backgrounds be available to all users when I install them via my account?  I placed some backgrounds into /etc/share/backgrounds (or /usr/share, can't remember exactly, and I'm not at the system. Whichever, it was the same directory that the default Ubuntu backgrounds were located in.) and I still had to go through the steps to manually add wall papers to this list, and when I logged into one of the other accounts, I had to manually install them all over again there.

2) I setup mount points for two of my WinXP partitions, and they are mounted on boot up correctly, and I can browse to them just fine.  However, I'd like to add them as mounted drives under the places flyout.  Is this possible, and if so, how?

3) Is there a good guide out there for administering a Linux system with multiple logins from one "non-root" account?

---

### Post by dare2dreamer on 2005-04-22
If you open and file dialog, select the folder/drive/etc and add it to the list o the left, it will show up in the places menu.

I agree that someone needs to make a saner interface for this. For the record, the file dialog thing is a front end for a file called .gtk-bookmarks in your home directory. As near as I can tell the format is:

file:///<pathhere>

And then the item shows up in the places menu.

As for administration, the first account on an Ubuntu system has sudo access, effectively giving it the power of root. So long as you have sudo priveledges, you should be able to do all sorts of dama...er, administration to the system.

You might also look into a command called su, which allows you to do things on a system as another user if you have their passwords (without having to log in as that user.). There is also a graphical variant of this under the system tools menu.

As for the theming thing, I'm not sure. I was always under the assumption that if you put something in /usr/share everyone had it. I'd imagine that there are settings in gconf to handle this...anyone else know for sure?

I do know that if you google for gnome system administrators guide, you'll find a big document with all sorts of information on how to admin systems for users with gnome desktops.

Happy hunting,

---

### Post by dare2dreamer on 2005-04-22
[http://www.gnome.org/learn/admin-guide/latest/](http://www.gnome.org/learn/admin-guide/latest/)

found it. it's a little out of date, but it's very useful.

---

### Post by BAshworth on 2005-04-22
[QUOTE=dare2dreamer][http://www.gnome.org/learn/admin-guide/latest/](http://www.gnome.org/learn/admin-guide/latest/)

found it. it's a little out of date, but it's very useful.[/QUOTE]

*bookmarked*

Thank you very much.  

Up until recently it was just me using Linux on this pc, so I never had to worry about it before.

---

