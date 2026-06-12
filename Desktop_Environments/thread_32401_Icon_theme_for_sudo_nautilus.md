---
title: "Icon theme for sudo nautilus"
date: 2005-05-07
forum: Desktop Environments
---

### Post by BAshworth on 2005-05-07
I have a launcher that opens up a nautilus window with root rights. (gksudo nautilus --browser)  However, the icon theme that is attached to root isn't one that I like.

I tried running sudo gnome-control-center and selecting it there, but that doesn't appear to stick.

I was planning on enabling the root account long enough to go in and make a few theme selections, and then disabling it again, but wanted to make sure I wasn't passing up a simpler solution.

Any other options?

---

### Post by MetalMusicAddict on 2005-05-07
[QUOTE=BAshworth]I was planning on enabling the root account long enough to go in and make a few theme selections, and then disabling it again.[/QUOTE]
Thats what I do sir. ;)

---

### Post by GTKpower on 2005-05-07
That's what I do as well.  

I have a little launcher in my panel that opens whatever I drag on to it as root, using the command: gksudo "gnome-open %u"

I have no problem with the icon theme when I'm in root, although my custom theme looks darker and not as nice.  The rest of the desktop (which is not in root) looks just fine.

No big deal.  I only open/run things in root when I need to.  I'm only in there for a minute at most.

---

### Post by MaX on 2005-05-07
[QUOTE=GTKpower]That's what I do as well.  

I have a little launcher in my panel that opens whatever I drag on to it as root, using the command: gksudo "gnome-open %u"
[/QUOTE]

```
Failed to run gnome-open 'file:///home/max/test.txt':
 Child terminated with 1 status
```
This is what I get when i do that... or should i specificaly use the "" signs?... apparently I do need those " signs... hmm...

---

### Post by GTKpower on 2005-05-07
All you need to know to create that launcher is right here:

[http://www.ubuntuforums.org/showthread.php?t=24008](http://www.ubuntuforums.org/showthread.php?t=24008)

Enjoy!

---

### Post by BAshworth on 2005-05-07
bah... got into a root account, set the icon theme to something other than hi-color (which uses the same icon for **everything**) and logged out.  Logged back in as my regular user, opened a nautilus window as root, and right back to hicolor.

Oh well, just an annoyance.

As for the launcher, for a while, I used a script that added "open file as root" to my right click options for a while.  However, it didn't work right if I needed to open a file with something other than the default program (ex.. xml files).  I prefer what I have now.

If anyone else wants it, create a launcher, and for the command put this in.

gksudo "nautilus --browser"      
including the quotes

or 

sudo nautilus --browser
no quotes needed.

One of the few things I missed from KDE (and it wasn't Firefox's fonts) was the File Browser - Super User Mode in the menu.

---

