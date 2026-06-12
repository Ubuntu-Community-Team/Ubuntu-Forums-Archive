---
title: "DOSBox directory"
date: 2005-09-14
forum: Gaming &amp; Leisure
---

### Post by andlinux on 2005-09-14
I installed dosbox with synaptic and I want to know where the directory is from dosbox so that I can install a front-end for it?

Somebody an idea ?

---

### Post by BoyOfDestiny on 2005-09-14
Hmm, I always use dosbox the old fashioned way... i think you can use synaptic, and right click on dosbox and choose properties (or something like that), and have it show you where it's installed.

---

### Post by Harleen on 2005-09-15
I don't have dosbox installed, so I can't tell you where it's installed. But you can easiely find it out for yourself by typing "which dosbox".

---

### Post by frank_b on 2005-09-15
Your post is a bit confusing and I'm not sure what you mean... but if you want to know where "dosbox" was installed, just go to Synaptic, right click on the dosbox package, choose "Properties" and it will show you in the "Installed Files" option which files were installed with that package and where they were installed.

In the version I have installed I see this:
[B]
/.
/usr
/usr/bin
/usr/bin/dosbox
/usr/share
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/dosbox.1.gz
/usr/share/doc
/usr/share/doc/dosbox
/usr/share/doc/dosbox/changelog.Debian.gz
/usr/share/doc/dosbox/THANKS
/usr/share/doc/dosbox/changelog.gz
/usr/share/doc/dosbox/README.Debian
/usr/share/doc/dosbox/copyright
/usr/share/doc/dosbox/NEWS.gz
/usr/share/doc/dosbox/README.gz
/usr/share/doc/dosbox/dosbox.conf.example.gz
/usr/lib
/usr/lib/menu
/usr/lib/menu/dosbox
[/B]
As you can see, with the exeption of the dosbox directory in "/usr/share/doc/" no directory was created just for this program. Personally, I created one in my home folder inside of which I installed another one containing one game ("Civilization").

When I want to run it, I just type "dosbox ~/dosbox/civ/CIV.EXE" or "dosbox ~/dosbox/civ/" and then "civ".

If by "front-end" you mean, for example, a short-cut in the tool bar, right click on it, choose "Add to Panel...", "Costum Application Launcher" and in the "Command" section put the dosbox command you use to run the game.

---

### Post by Ensnared on 2005-09-15
Seems like he means "which directory is 'mounted' as C:\ inside Dosbox?" - atleast that's how I read it, and I'm slightly curious about that myself :)

---

### Post by andlinux on 2005-09-15
[QUOTE=frank_b]Your post is a bit confusing and I'm not sure what you mean... but if you want to know where "dosbox" was installed, just go to Synaptic, right click on the dosbox package, choose "Properties" and it will show you in the "Installed Files" option which files were installed with that package and where they were installed.

In the version I have installed I see this:
[B]
/.
/usr
/usr/bin
/usr/bin/dosbox
/usr/share
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/dosbox.1.gz
/usr/share/doc
/usr/share/doc/dosbox
/usr/share/doc/dosbox/changelog.Debian.gz
/usr/share/doc/dosbox/THANKS
/usr/share/doc/dosbox/changelog.gz
/usr/share/doc/dosbox/README.Debian
/usr/share/doc/dosbox/copyright
/usr/share/doc/dosbox/NEWS.gz
/usr/share/doc/dosbox/README.gz
/usr/share/doc/dosbox/dosbox.conf.example.gz
/usr/lib
/usr/lib/menu
/usr/lib/menu/dosbox
[/B]
As you can see, with the exeption of the dosbox directory in "/usr/share/doc/" no directory was created just for this program. Personally, I created one in my home folder inside of which I installed another one containing one game ("Civilization").

When I want to run it, I just type "dosbox ~/dosbox/civ/CIV.EXE" or "dosbox ~/dosbox/civ/" and then "civ".

If by "front-end" you mean, for example, a short-cut in the tool bar, right click on it, choose "Add to Panel...", "Costum Application Launcher" and in the "Command" section put the dosbox command you use to run the game.[/QUOTE]

That's what I meant, it's stored in /usr/bin/, now I can tell dosboxer where he can find dosbox.

---

### Post by andlinux on 2005-09-15
I'm using the pydosbox frontend for dosbox now  this program is easy to use. 
It's written in python.

pydosbox: [http://www.panayotis.com/pydosbox/index.html](http://www.panayotis.com/pydosbox/index.html)

---

### Post by frank_b on 2005-09-15
OK then. "Gotcha".

In your terms then, the "dosbox directory" is the "/usr/bin/" one, since the program itself it's just the "dosbox" file that was installed in this directory and besides the "doc" and "man" files, I just checked, the dosbox file in "/usr/lib/menu/" seems to be apparently just a reference to the Debian menu.

I had never heard of a front-end program for dosbox, so I though you might be a newbie like myself and be using the term incorrectly. Sorry.  :neutral:

---

