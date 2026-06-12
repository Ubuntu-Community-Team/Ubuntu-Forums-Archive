---
title: "Gtk Icons in Fluxbox"
date: 2006-01-06
forum: Desktop Environments
---

### Post by jd_k on 2006-01-06
I'm sure I'm simply overlooking something incredibly obvious, but here goes:

I'm running fluxbox at the moment, and have been using Nautilus as a file manager. My basic problem is that my Nautilus icons are terrible (folder icons, file icons, etc). I can change them with gnome-theme-manager, and all is well. But when I kill the gnome-settings-daemon, they revert back to the ugly versions. I figure that Nautilus is obviously using something like a "default" icon set in the absence of information from the settings-daemon. My question is: how do I change that default icon set?

I found an icon set installed in my /usr/share/icons directory that looks identical to what I'm getting in Nautilus (incidentally, it's called "crystalsvg"). However, replacing the contents of the folder those of another icon set and restarting Nautilus doesn't fix anything. I'm guessing that means those aren't the files Nautilus is pulling for its icons.

I'm sure the answer is as easy as locating a pointer in a configuration file or isolating a particular directory where the icons are stored, but I haven't been able to figure it out.

Thank you,
~Joshua

---

### Post by KiLVaiDeN on 2008-02-24
Hello,

It seems this problem is recurring, even with other Linux distributions.

GTK is not really "windows manager" friendly, and therefore, you need to configure some files, in order to make it work with, let's say "Fluxbox" for example.

An easy way to fix the problem, for now, until I've found a better one if I have time, is to simply load Banshee. Banshee has a loading process which includes the loading of your favorite GTK themes, so it'll do the trick.

I heard ( opensuse related ) that some "political" things are going under, maybe it's a little bit complex for them to make it an easy shot for windows managers other than Gnome. 

Just load Banshee for now, until this problem is widely resolved and a better solution is found, you can then close it again, and your GTK icons will be loaded.

Cheers
K

---

### Post by kerry_s on 2008-02-24
you need to create a ~/.gtkrc-2.0 file to put your gtk theme name to have it load.
gtk-icon-theme-name = "Tango"
for theme+icons
gtk-theme-name = "Tango"

replace "Tango" with "your-theme-name"

[http://fluxbox.sourceforge.net/docbook/en/html/](http://fluxbox.sourceforge.net/docbook/en/html/)

---

