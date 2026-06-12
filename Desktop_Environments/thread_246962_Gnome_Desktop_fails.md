---
title: "Gnome Desktop fails"
date: 2006-08-30
forum: Desktop Environments
---

### Post by wonderboy2005 on 2006-08-30
Hi everyone, 

First of all, I'd like to say I really like Ubuntu.  It is by far the easiest linux distro I've used, and the first that I've found to be more valuable than the hard drive space it occupies.  

Having said that, I'm having a bit of a problem.  I installed Kubuntu a couple weeks ago.  Soon after I decided that I would like the Gnome Desktop better, so I installed the ubuntu-desktop package.  All was fine and dandy, and I was enjoying my newly-installed operating system.  That is, until two days ago.  

[here comes the actual problem]

Gnome has recently failed to load properly.  It begins the loading process, goes through the splash screen and tells me what its starting (Nautilus, etc), then begins to display the two bars (taskbars?) at the top and bottom.  This is where it all goes south.  the two bars will disappear and reappear several times, ending with an error text box with no text in it.  

I've since reverted back to the KDE desktop and it seems to work fine, but I'd rather use Gnome.  Thus far, I've tried uninstalling/reinstalling Gnome, switching window managers (KDE at the moment), reinstalling the X server, dpkg-reconfigure the x server, dpkg-reconfigure gnome, and reverting to the 'nv' display driver, all to no avail.  

Any suggestions would be much appreciated.
-Wonderboy

---

### Post by croak77 on 2006-08-30
Try deleting all the .gnome .gnome2 .gconf .gconfd folders in your home directory.

---

### Post by wonderboy2005 on 2006-08-30
Thanks a lot.  That did the trick.  I tried something like that earlier, but I apparently didn't get all the folders.  Anyways, thanks again for the help.

---

