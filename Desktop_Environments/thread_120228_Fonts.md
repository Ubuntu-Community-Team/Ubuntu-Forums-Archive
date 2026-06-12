---
title: "Fonts?"
date: 2006-01-21
forum: Desktop Environments
---

### Post by dk_pa on 2006-01-21
----Eh...Sorry this should have been in the GNOME Desktop section.  I clicked the wrong link and didn't even realize it.  Maybe someone can move it for me.  Thanks----

I need some help with fonts.  This is all spurred because I can't run GNUCash or XNC because they can't find the Helvectica font(s).  I really scratch my head that a program bombs because it uses a special font and not just whatever is set as default but that is entirely different conversation.

Anyway, I can't quite make out how all the fonts are setup and organized.  I thought I was going to fix things by adding the type1 fonts and making sure that my xorg.conf file had that part uncommented out and the folder was correct etc.  That didn't do it.  So then i'm looking through the System -> Pref -> Font and click on "Font Folder" and see all these fonts that I assume it's reading from the /usr/share/fonts/font.dir Which is fine, but what's with X having part of the config for /usr/x11r6/lib/fonts  or wherever it's looking in xorg.conf 

Anyway that was just me being curious about the setup =)
My problem is that I'm not sure what to do about the Helvectica font tho.  Can I rip it off a windows box and just throw it in the msttcorefonts directory ro do I have to do something special to install a new font and is it what GNUCash is looking for?  

Thanks for the help...here is the GNUCash crash from Term as reference...

```

Warning: gnucash_style_set_register...(): Cannot load font: -adobe-helvetica-medium-r-normal--*-120-*-*-*-*-*-*

Fatal Error: gnucash_style_set_register...(): Cannot load fallback font: -adobe-helvetica-medium-r-normal--*-120-*-*-*-*-*-*

Warning: gnucash_style_set_register...(): Cannot load font: -adobe-helvetica-medium-o-normal--*-120-*-*-*-*-*-*

Fatal Error: gnucash_style_set_register...(): Cannot load fallback font: -adobe-helvetica-medium-o-normal--*-120-*-*-*-*-*-*

Fatal Error: gnucash_style_set_register...(): Cannot load fallback font: -adobe-helvetica-medium-r-normal--*-120-*-*-*-*-*-*

Fatal Error: gnucash_style_set_register...(): Cannot load fallback font: -adobe-helvetica-medium-o-normal--*-120-*-*-*-*-*-*

```

---

### Post by Michael Steinberg on 2006-01-21
This is a common question--because GNOME is frankly a little lame about fonts--and the posts at [http://ubuntuforums.org/showthread.php?t=119603](http://ubuntuforums.org/showthread.php?t=119603) can give you answers and a link to the Wiki.

---

### Post by dk_pa on 2006-01-23
Thanx for the links it helped a lot.  I am, however, quite confused still about the Adobe Helvectica font problem.  I copied all the fonts for the Adobe stuff to /home/user/.fonts but that didn't do anything.  I also added 

```
FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
``` 

to my xorg.conf file making sure the fonts were there and logged out and back in and GNUCash is still GNUCrash.  I did that because of looking through the buzilla stuff at GNUCash's website.  Take a look if you guys want.

[http://bugzilla.gnome.org/show_bug.cgi?id=110808](http://bugzilla.gnome.org/show_bug.cgi?id=110808)

---

