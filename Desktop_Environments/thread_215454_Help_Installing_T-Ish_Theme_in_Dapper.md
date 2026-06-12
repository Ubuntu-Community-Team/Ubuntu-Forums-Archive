---
title: "Help Installing T-Ish Theme in Dapper"
date: 2006-07-14
forum: Desktop Environments
---

### Post by Ben Logan on 2006-07-14
Hi Folks, 

By following Trocip's advice in the how to:Make Gnome look like OS X thread, I've got the basic T-ish theme up and running.  Cool!  However, I've been struggling for hours to get the other "theme's within a theme" choices listed under "Contents" in the text below, to appear in under the System/Preferences/Theme dialog.  

The following (in bold type) is from T-ish's website, explaining what comes with the .tar.gz file: 

[B]
Contents:
T-ish - Clearlooks theme
T-ish Aguastyle - Clearlooks theme with some pixmap elements
T-ish-Ubuntulooks - Ubuntlooks theme
T-ish-Ubuntulooks Aguastyle - Ubuntulooks theme with some pixmap elements
T-ish-Ubuntulooks Graphite - same as above but thanks to Alejandro Cornejo

Based on Clearlooks or Ubuntulooks engines, Ish GTK theme with additional buttons from Expose and GlossyP metacity borders (many with thanks to authors).

Requires clearlooks or ubuntulooks engine.

For best results use OSX icons, jaguarx mouse theme, and FoxiTiger firefox skin (links below).

IMPORTANT: In order to install all of the themes you'll have to manually extract to ~/.themes dir.[/B]

Do I have to install the "Clearlooks or Ubunulooks Engines" in Dapper?  I looked under synaptic package management and can't find them.  Also, how the heck do I "manually extract to ~/.themes dir."  I tried opening the .tar file with the archive manager, but have no luck selecting the destination suggested by the author.  

Help me out so I can sell my Mac!

---

### Post by Ben Logan on 2006-07-14
Ok, problem solved.  I'm new to Linux - probably completely obvious based on my post above!  

If anyone downloads the latest T-ish Pack and like me, installs it, and is disappointed that he or she can't access the "Ubuntulooks Graphite" variation, you can save yourself above three hours and download this one from  Gnome-look.org:

[http://www.gnome-look.org/content/show.php?content=41732](http://www.gnome-look.org/content/show.php?content=41732)

Just drop this in the system/preferences/theme dialog and you're good to go.  You wont believe you're not on a Mac.  :mrgreen:   Thank you T-ish!

---

### Post by ayoli on 2006-07-14
yes, tmilovan t-ish's are really great themes, even if i mod it a bit :p
Ben Logan: if you want a wide install of your theme (ie: installed in /.themes and running nautilus as root: you'll not see yoiur theme on this nautilus window) then install your theme pack to /usr/share/themes/ , then all users on your computer can use it.
another way if you're the only user with root is to link your ~/.themes to /root (as root: sudo ln -s ~/.themes /root/).
welcome to linux, have fun,
regards.

---

### Post by Ben Logan on 2006-07-16
> **ayoli said:**
> yes, tmilovan t-ish's are really great themes, even if i mod it a bit :p
Ben Logan: if you want a wide install of your theme (ie: installed in /.themes and running nautilus as root: you'll not see yoiur theme on this nautilus window) then install your theme pack to /usr/share/themes/ , then all users on your computer can use it.
another way if you're the only user with root is to link your ~/.themes to /root (as root: sudo ln -s ~/.themes /root/).
welcome to linux, have fun,
regards.

Thanks Ayoli.  I'm afraid the only way I know how to install a theme is the wonderfully simple method of dragging the tar over to the theme dialog box and answering "yes" when asked if I want to install.  Your nice instructions, are over my head, being such a newb.  

I'd still be interested in learning how to follow the directions tmilovan laid out, if anyone cares to walk me through.  ;)

---

### Post by tmilovan on 2006-07-20
Hello Ben Logan, thanks for kind words Ayoli,

Ben,
The only way to have all themes from t-ish pack installed is to extract them manually to your .themes folder. 

Here is the easiest way:
1. save t-ish pack to desktop
2. right click on it -> extract here
3. select all extracted folders -> right click on them -> cut
4. start file manager -> right click on it -> show hidden files
5. goto .themes folder in your home
6. right click -> paste into
7. now go to themes chooser and select t-ish flavour you like

Hope it helps.

Toni

---

### Post by ardchoille on 2006-07-20
The theme installer in the theme manager doesn't do a good job of installing multi-theme packages. It's always best to unpack the theme to /usr/share/themes or ~/.themes.

---

