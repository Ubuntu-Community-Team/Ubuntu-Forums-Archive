---
title: "Repeated app crash"
date: 2006-06-16
forum: Desktop Environments
---

### Post by pratzabrat on 2006-06-16
Hi! I have been using the Anjuta C++ IDE for quite sometime. Just a while back when I tried to remove some toolbar items I dint want, Anjuta closed automatically. My subsequent attempts to open Anjuta gave the a dialog box with the following message :
> The Application "anjuta" has quit unexpectedly.

You can inform the developers of what happened to help them fix it.  Or you can restart the application right now.
There are options for restart/close/inform developers. I tried restart, but it again gives me the same dialog box. Close simply closes the app. 

So I reinstalled Anjuta after deleting all the configuration files in my home dir. But still the problem persists. Please do help, I am being chased by a deadline. Thanks!!!

---

### Post by pratzabrat on 2006-06-17
Hey pls do hv a look at this problem... i m contemplating a reinstall if things dont work out fine..  thanx!!!

---

### Post by vasdee on 2006-06-22
try starting anjuta from the command line.When it crashes, with any luck it will print out something useful which we can use to debug

---

### Post by geoffkaniuk on 2006-07-31
Hello vasdee,

I have experienced exactly the same crash with Anjuta 1.4 - trying to detach one of the toolbars.

Firsly when detached, it could not be moved or sized.  Back in Anjuta I tried to switch it back on in the View menu.  Anjuta Crashed.

Tried to restart - it crashes.  Try to close and relaunch - crashes.

I ran anjuta from the command line.  

By the way I tried the command $ anjuta > temp hoping to get the output in a file - but the file was empty.  So here is a verbatim copy from the terminal:

** Message: Initializing AP class
** Message: Initializing AP instance
** Message: Initializing launcher class

(anjuta:5905): Gtk-CRITICAL **: gtk_widget_hide: assertion 'GTK_IS_WIDGET (widget)' failed

I hopes this helps to sort out the problem, as Anjuta looks good.

I come from a Borland Builder/MSVC/XP background but am pretty new to Linux.

Thanks - Geoff:?: :?:

---

### Post by Mr. Picklesworth on 2006-12-24
I'm a bit late here, but I may as well say a possible fix.
I had this problem when I decided to play around with detachable menubars and toolbars in Gnome. (Incredibly nice feature, by the way!)

Most programs are using older libraries or something, so they don't give me the full experience (though I can still amuse myself at least with changing menu accelerators). However, I recently started playing with Gnome-MUD, which to my glee has detachable menu bars!
So I started playing with it and I detached the menu bar and everything went fine. Then I closed it (actually can't remember if it crashed. I don't think it did, though), and reopenned to see if it remembered the position of my menu. At this point the toolbar had been reattached but the menu had not.

It still loaded and ran, and I could use the menu. *However*, as soon as I tried dragging the menu anywhere (I didn't like where I had put it), the program crashed.

I tried deleting the program's config directory in my home folder, and that didn't work. Then I realized that the magical dragging of menu bars is Gnome, so I checked .gnome2 in my home folder. There I found a file called gnome-mud which contained the remembered position of my menu bar. I deleted that file, and it all worked again.

So, if you encounter this, look for your program's name in .gnome2 or maybe .gnome within your home folder.
Is this a bug in Gnome, do you think?

---

