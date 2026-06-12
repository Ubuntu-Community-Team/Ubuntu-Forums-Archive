---
title: "Changing the panel/menubar icon......."
date: 2007-05-14
forum: Desktop Effects &amp; Customization
---

### Post by Izobalax on 2007-05-14
OK, I've had a look around for this one. It seem the main method, via the conf-editor doesn't work. I've tried the 'sudo mv' method as well and that doesn't work. Is it because I use Feisty?

Here's a shot of my current menu bar. Note that I use the OS X Mod icon set from gnome-look here ---> [LINKY](http://www.gnome-look.org/content/show.php/OsX_MoD?content=54851)

[IMG]http://i14.photobucket.com/albums/a319/Shakhtar9/menubar1.png[/IMG]

I wish to replace the apple icon with this one....

[IMG]http://i14.photobucket.com/albums/a319/Shakhtar9/29218-ubuntu.png[/IMG]

I already have this icon shrunk to 24x24 with transparency. 

Has anyone managed to work around this one yet?

/izo

---

### Post by bashologist on 2007-05-14
What's the problem? You are able to change the icon? Is the problem transparency maybe? Did I miss something, or did you not explain?

---

### Post by Izobalax on 2007-05-14
> **bashologist said:**
> What's the problem? You are able to change the icon? Is the problem transparency maybe? Did I miss something, or did you not explain?
Oh, I explained. :grin:

See that apple icon in my menu bar? I want to replace it with the Ubuntu icon I posted. I've already shrunk the ubuntu icon down to 24x24 with transparency, and I've tried several methods of replacing the apple icon, with no luck.

This is the problem. 

/izo

---

### Post by honeybear on 2007-05-14
> **Izobalax said:**
> OK, I've had a look around for this one. It seem the main method, via the conf-editor doesn't work. I've tried the 'sudo mv' method as well and that doesn't work. Is it because I use Feisty?

Here's a shot of my current menu bar. Note that I use the OS X Mod icon set from gnome-look here ---> [LINKY](http://www.gnome-look.org/content/show.php/OsX_MoD?content=54851)

[IMG]http://i14.photobucket.com/albums/a319/Shakhtar9/menubar1.png[/IMG]

I wish to replace the apple icon with this one....

[IMG]http://i14.photobucket.com/albums/a319/Shakhtar9/29218-ubuntu.png[/IMG]

I already have this icon shrunk to 24x24 with transparency. 

Has anyone managed to work around this one yet?

/izo
Is there the exact same for fluxbox ... 
Linther isnt that good ...:-(

---

### Post by Izobalax on 2007-05-14
FIXED!

OK, as a reminder mainly for myself, I realised that since the "distributor-logo" icon was decided from the icon theme currently in use (and I'm using the OsX Mod theme), then I had to change the icon in that icon pack. Eventually I found the apple icon in question. So, I shrunk the ubuntu icon I had to 48x48 (24x24 was too small), renamed it to "distributor-logo.png", copied it, went to my home and then .icons, found the OsX Mod folder, found the apple icon currently serving as the "distributor-logo.png" and replaced! :grin:

Done! Here's what it looks like now......

[IMG]http://i14.photobucket.com/albums/a319/Shakhtar9/fixed_menubar1.png[/IMG]

/izo

---

### Post by valke on 2007-05-15
how do you determine what icon it is defaulting to? i'm currently trying to customize my desktop to look like *groan* vista, and cannot seem to change it. please do help.

---

### Post by Izobalax on 2007-05-15
> **valke said:**
> how do you determine what icon it is defaulting to? i'm currently trying to customize my desktop to look like *groan* vista, and cannot seem to change it. please do help.
What icon set are you using? Check in the Themes. :)

/izo

---

