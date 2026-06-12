---
title: "Modify trash applet"
date: 2009-01-26
forum: General Help
---

### Post by Dirjel on 2009-01-26
I want to change the behavior of the trash applet on the Gnome panel.  By default, when you click it, it opens the trash folder with whichever file browser is your default (presumably via the command "xdg-open trash:///).

I want the trash applet to use "thunar trash:///" when I click on it, because I like Nautilus for standard browsing, but I want Thunar for looking in my trash, because Thunar has a restore option.

ATM, I'm using the standard trash applet, and I have a launcher right next to it, because neither is good enough by itself.

Anyway, I found what I believe to be the applet, but I have no idea how to modify it.  It was located at /usr/lib/gnome-applets/trashapplet, and I think it's a binary, and not a script or something that I can just open up and change.

---

### Post by mb_webguy on 2009-01-27
What version of Ubuntu are you using?  I ask because I'm using Intrepid and my version of nautilus has a restore from trash option.  If you're using hardy, you may want to try installing the [Intrepid version of nautilus]("http://packages.ubuntu.com/intrepid/nautilus").

EDIT:  You could also follow the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=893891") to add the functionality in nautilus using a script.

---

### Post by Dirjel on 2009-01-27
Oh look, you're right.  Yeah, I have Intrepid, but I SWEAR that wasn't there last time I checked.

Thanks XD

---

