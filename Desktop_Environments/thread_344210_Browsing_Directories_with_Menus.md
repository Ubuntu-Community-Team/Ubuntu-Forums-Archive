---
title: "Browsing Directories with Menus?"
date: 2007-01-22
forum: Desktop Environments
---

### Post by NotPhil on 2007-01-22
Is there an program or panel applet that will allow me to browse through file directories with a hierarchical menu?

I just moved over to Ubuntu from a Mac, and I really miss being able to drop a folder into the Dock and then getting a menu listing that folder's contents by clicking on the folder. Older Macs had a similar feature in the Apple menu. If the folder contained other folders, they would be listed as sub-menus.

I've looked around for Panel add-ons and Dock replacements, but I couldn't find anything that would automatically create a menu from the directory structure. Does anyone know of anything like this for Ubuntu/GNOME?

---

### Post by Pobega on 2007-01-22
I believe Thunar has the option to have a tree menu instead of a shortcut menu.

[[IMG]http://img261.imageshack.us/img261/127/tree3ri.th.jpg[/IMG]](http://img261.imageshack.us/img261/127/tree3ri.jpg)

If that isn't what you're talking about then try to be more specific.

---

### Post by NotPhil on 2007-01-22
> **Pobega said:**
> I believe Thunar has the option to have a tree menu instead of a shortcut menu.

Thanks, but Nautilus can already display directories with a tree diagram, by selecting "view as list" from the "view" menu. I was looking for something that would display directory files in a menu with sub-menus for nested directories and their files ...

[IMG]http://www.math.uwaterloo.ca/mfcf/documentation/mac-osx/dock/Folder.jpg[/IMG]
[IMG]http://www.sigsoftware.com/classicmenu/screenshot.jpeg[/IMG]
[IMG]http://www.desktopboosters.com/scr/Desktop400.gif[/IMG]

---

### Post by Pobega on 2007-01-22
Oh, if you're using Gnome you can edit your places drop down menu, but that doesn't let them fan out the directories. I don't know what else to say, I can't think of anything myself.

---

### Post by NotPhil on 2007-01-25
I finally found one. Only Red Hat seems to have a binary package of it, but I'll see if I can build it from source. It's called [PanelFM.]("http://panelfm.sourceforge.net/")

---

### Post by rko618 on 2007-02-24
the closest thing I know of is changing Nautilus' default behavior from "view as icons" to "view as list".  But no luck on the desktop browsing feature.

---

### Post by floke on 2007-02-24
Hmm, that does look nice. Shame we ain't got it.

---

### Post by NotPhil on 2007-02-24
> **Steve.K said:**
> Hmm, that does look nice. Shame we ain't got it.PanelFM will compile and run without problems, but it needs some work. Shell scripts and desktop launchers will open in a text editor instead of running, and opening a directory with it is clunkier than it needs to be.

I suppose someone could write a Nautilus extension to do this sort of thing, but it looks like that's beyond me. Do the Nautilus developers consider feature requests?

---

### Post by disturbedite on 2007-02-24
i've been looking for something just like this for kde's kicker/konqueror/ksmoothdock since i'm on kubuntu....i've had no luck so far.  i sure miss it from using objectdock on win...i use ksmoothdock (i maintain the deb package for the author) and i hope that this will be possible in the future.

---

### Post by NotPhil on 2007-02-27
> **disturbedite said:**
> i sure miss it from using objectdock on win...Those fly-out menus look nifty ...

[IMG]http://www.stardock.com/products/objectdock/odock-july05b.jpg[/IMG]

You'd think with all the Compiz/Beryl eye-candy development going on right now, someone would try to add impressive-looking file-access to the mix.

---

