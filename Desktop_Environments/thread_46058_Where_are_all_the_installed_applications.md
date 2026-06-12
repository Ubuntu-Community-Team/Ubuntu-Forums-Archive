---
title: "Where are all the installed applications?"
date: 2005-07-03
forum: Desktop Environments
---

### Post by DancingSun on 2005-07-03
Ok, this is my 4th day of Ubuntu.

Synaptic is living up to my expectations in making Linux applications management easy.  Actually, I think it is even better than the Windows installer scheme.

Here are my concerns/questions:
[list=1]
[*]Where do all my applications go?  Some applications that I install will appear in the Gnome applications menu, and some don't.

[*]Where are the applications installed in the file system?  Which directories?  The reason I'm asking this is that I made a separate partition for the "/home" directory, and I only gave 5GB to the "/" directory.  If the applications are all going to the "/" directory, I'm thinking I might run out of space soon, and may need to resize the partitions or reinstall Ubuntu (yikes!).

[*]Is there a way to specify where I want the application item go on the menu?
[/list]

---

### Post by argux on 2005-07-03
hi, I hope you're liking ubuntu. I'm quite new myself and I'm loving it.

1. If it's a terminal application (no graphical interface) it won't show up in the menu. You can open a terminal and use it from there. If it's a graphical application, and it doesn't show, I think you can restart gnome (just gnome, not the computer) and they might show. If they still don't appear, you can add it manually.

I remember reading a thread about this issue not too long ago, but now I can't find it. Maybe you can.

2. My / partition is also 5GB. I think I've got everything I need (and a bunch of useless stuff that I don't really need) and it's only 57% full. Maybe if you install a lot of games you can quickly fill it, but if you're concerned because in windows an office suite can fill hundreds of megabytes, this is almost never the case in linux. Check in the lower part in synaptic. It will tell you how much space the new packages will take.

3. Yes, there is. You can install smeg. It's a menu editor for gnome. It's very simple and works well, though it can't find programs automatically. It's still very much worth it. You can add entries, add submenus and move things around. Try it!

I hope that helps, cheers!

---

### Post by DancingSun on 2005-07-03
Thanks for the quick response!

It sure cleared some confusions and worries that I have with Ubuntu!

I installed gxine and was wondering why it didn't show up on the applications menu.  Seems like it's not a bug that something like this would happen.  I had manually added the application to my top gnome panel, which works fine as well.

---

### Post by dewey on 2005-07-03
Installed applications go into /bin /sbin /usr/bin /usr/sbin, unless otherwise specified during compile.

To kill gnome panel to refresh, and hopefully see new launchers in menu, use $killall gnome-panel, and to manually add new files, use smeg, [http://ubuntuguide.org/#menu-editor](http://ubuntuguide.org/#menu-editor)

And 5gigs should be good for the root partition, if /home is on it's own.  Cedega games install to your home directory, so windows games shouldn't take up root partition room atleast.

---

### Post by DancingSun on 2005-07-03
[QUOTE=dewey]Installed applications go into /bin /sbin /usr/bin /usr/sbin, unless otherwise specified during compile.[/QUOTE]
Ah! So that's where they're hiding!

> And 5gigs should be good for the root partition, if /home is on it's own.  Cedega games install to your home directory, so windows games shouldn't take up root partition room atleast.
Sweet!  I have 75GB for "/home"!

---

### Post by doclivingston on 2005-07-03
[QUOTE=dewey]Installed applications go into /bin /sbin /usr/bin /usr/sbin, unless otherwise specified during compile.[/QUOTE]

Executables go there, most applications have data that is stored in /usr/share/applicationname. In Synaptic you can get a list of what files are put where, by right-clicking on a package, going to properties and the "Installed Files" tab (this only works once it's installed though).

5Gb for you root partition is usually fine when you have a seperate /home partition, unless you install some really big games into your root partition (like UT2004 or something).

---

### Post by Soulfly on 2005-07-03
I run the KDE desktop and I have used the "kappfinder" (enter this is "Run Command..") to add a few applications that not appeared in the menu. It will scan for applications and present you with a new menu where you can select which applications you want to be added to it.

---

### Post by t2kburl on 2005-07-03
Thanks for the kappfinder suggestion ....  I found apps I forgot I had   :???:

---

