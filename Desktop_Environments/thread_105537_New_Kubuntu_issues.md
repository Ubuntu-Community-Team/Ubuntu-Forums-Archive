---
title: "New Kubuntu issues"
date: 2005-12-18
forum: Desktop Environments
---

### Post by Maelgwyn on 2005-12-18
Hey all :)

I've just installed Kubuntu Breezy Badger :KS, and I've encountered a couple of issues:

* When I try to run Adept, I get the little bouncing icon, but it never loads...
* I've downloaded the latest Firefox, but I can't run it! I click on the firefox icon in the firefox folder, and nothing happens... 
* Whenever I try to install anything, I get this:
```

W: Couldn't stat source package list http://nz.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://nz.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://nz.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://nz.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

```

Has anybody got some ideas for a poor n00b from NZ? :D

---

### Post by Kadin2048 on 2005-12-19
I have not gotten Adept to work under Kubuntu. I could be wrong, but maybe it's a Gnome-only app? I did use it before I switched from Gnome->KDE, so I know it did work on my system originally. But now I get the same thing, it refuses to open. I didn't fuss with it too much though; I just use one of the other package managers instead.

The "couldn't stat source package list" errors can sometimes be corrected by running 'sudo apt-get update' to refresh the package lists. I'd try that at least for starters, if you haven't already.

---

### Post by aysiu on 2005-12-19
Try the first link in my sig.

---

### Post by GeneralZod on 2005-12-19
[QUOTE=Kadin2048]I have not gotten Adept to work under Kubuntu. I could be wrong, but maybe it's a Gnome-only app? [/QUOTE]

Hehe - no :) Adept is intended to be the KDE version of Synaptic, and its development is sponsored by Canonical, so one would hope that it would work best under Kubuntu ;)

However, it is a young project with (I think) just one developer on it, which explains a lot of the difficulties people have with it.

---

### Post by Maelgwyn on 2005-12-19
[quote=aysiu]Try the first link in my sig.[/quote]

Awesome thanks for that :) That's done the trick!

---

### Post by Rackerz on 2005-12-19
Adept always mis-fires for me on the first try of loading it up, just click it again and it should load, always does for me ;). Handy little thing it is i prefer it over Synaptic.

---

