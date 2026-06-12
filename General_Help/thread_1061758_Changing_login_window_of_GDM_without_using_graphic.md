---
title: "Changing login window of GDM without using graphical tools?"
date: 2009-02-06
forum: General Help
---

### Post by GrfyGrumpyBear on 2009-02-06
How? I'm setting up a pc for someone, and I want to give them a customized-from-scratch (alternate) install. They want a certain GDM theme, and I don't have the GUI tools.

---

### Post by spiderbatdad on 2009-02-06
I was able to do this a couple of years ago, though it took some patience and trial and error. The files for the themes are located in /usr/share/gdm/themes.
You can pretty much get the jist of things by studying those files. Some snags I ran into had to do with naming files. For example "GdmGreeterTheme.Desktop" had to be named just like that. Then, too the structure of that file has to be precise. So you can also look at other GdmGreeterThemes and see how they are made. When you get to mixing and matching pieces, that's where some aspects of the files can get changed and cause the theme not to work...hence the patience.

---

### Post by GrfyGrumpyBear on 2009-02-07
True, that's good but how to I actually *set* the theme?

---

### Post by spiderbatdad on 2009-02-07
once you have a valid gdm theme directory in the folder /usr/share/gdm/themes, your new theme will show up in the list under System>>Administration>>Login Window>>Local. Select it there with the radio button.

Beyond that gdm isn't really set up for file type editing for configuration. You can go ahead and run ```
 gdmsetup 
``` which will launch the graphical login window selection tools. There is also some way to run gdmthemetester, I can't recall...but why when you have the graphical tools? A rhetorical question. I would be glad to know myself if you find a way to actually set the theme entirely from the command line.

---

### Post by GrfyGrumpyBear on 2009-02-09
Because the graphical tools are far too bloated for my liking and I want just IceWM and GTK+. No GNOME desktop. So this way everything is faster. However, this graphical tool is installed with just GDM?

---

