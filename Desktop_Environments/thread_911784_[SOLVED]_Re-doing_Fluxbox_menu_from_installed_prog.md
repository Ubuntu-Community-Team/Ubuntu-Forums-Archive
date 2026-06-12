---
title: "[SOLVED] Re-doing Fluxbox menu from installed programs question"
date: 2008-09-06
forum: Desktop Environments
---

### Post by Hooya on 2008-09-06
I use fluxbox on my Ubuntu 8.04 install.  I still have the Gnome desktop handy for when things don't work in Fluxbox and I can't get them to work handy (like, many Wine apps don't want to work in Fluxbox).  But I use Fluxbox for my day to day use because it's faster and I don't need a lot of the Gnome stuff running all the time.

My problem though is that sometimes I'll install a program and won't know how to run it - meaning I won't know the command for it.  Sometimes it's not apparent based on the application name, especially if it's a suite, what the actual command to run is.  This is especially true with Wine apps and things like OpenOffice and Ubuntu Studio applications.

I use a customized right click menu that has things organized how I like them, which is nice, but it doesn't automatically add applications to that menu anywhere when I install a new program.  If I add the program in Fluxbox it still shows up in the Gnome panel menu, so I know the entry is being added to some collection of shortcuts.  I would like to know if there's a way that I can update my Fluxbox menu based on the Gnome panel menu and then make any customizations from there.

Any thoughts or ideas?  I'm OK if it screws up my custom menu, since it's easy to move things around, but I can't add applications if I don't know their commands - plus that could take a long time.

---

### Post by RedSquirrel on 2008-09-06
Have a look at the tutorial in my signature.

/etc/X11/fluxbox/menudefs.hook should be recreated automatically every time you install a new application. Not all of your applications will be in there, but many will be.

You can also use the fluxbox-generate_menu script and regenerate the menu when you install applications.

You may still have to add some things manually to the menu now and then.

---

### Post by Hooya on 2008-09-07
Thanks!  That does help.

I kind of took that first thought and ran with it a bit.  I found that if I did a submenu that does this:
```
[include] (/etc/X11/fluxbox/fluxbox-menu)
``` then I'll always have the contents of the default generated menu in my custom menu.  I can edit my customs but I'll always have the default menu handy for newly made stuff as long as I do the update-menu command every now and then.

This actually changes my concept on how to customize the menu, since now I can get rid of a lot of extraneous things, and just keep my most commonly used programs in the custom menu, with less common things in the "all applications" part of my menu.

The one thing this doesn't solve is my problem with Wine.  The Wine install programs show up in the Gnome task menu just fine, but they don't in the Fluxbox menu.  And when I copy some of the commands over they don't always work in Fluxbox.  I will mark this thread as solved, but that one lingering question remains.

---

### Post by RedSquirrel on 2008-09-07
I haven't used Wine in a long time so I can't help with that part.

If you haven't already done so, it might be worthwhile to start a new thread to address specifically your difficulties using Wine with Fluxbox (e.g., why the commands don't always work).

---

