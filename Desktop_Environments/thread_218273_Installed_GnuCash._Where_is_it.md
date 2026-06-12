---
title: "Installed GnuCash. Where is it?"
date: 2006-07-18
forum: Desktop Environments
---

### Post by mjpatey on 2006-07-18
Hi, Group-

I honestly didn't think I'd get this far with Linux... but I've really been pleasantly surprised by it, enough to start thinking, "I wonder if I can really do *everything* I need in Ubuntu?"

On my list of "I bet there's no Linux equivalent to ______" was financial software (such as Quicken or MS Money).  Immediately Google turned up GnuCash ($0) and Moneydance ($30).

So I went into Synaptic and downloaded and installed GnuCash.  The only problem is, even after a reboot (not usually necessary, I realize), I don't see GnuCash anywhere in my system.  After exploring the Gnome "Applications" menu to no avail, I did a search of the entire File System, and turned up only a few PNG files and a small XML file.

Anybody have an idea what happened, or where I can find my application?

Thanks for any help you may have!

-Mark

---

### Post by jordilin on 2006-07-18
You can just type in the command line
```
gnucash &
```
If you want the icon, go to applications->accessories->Alacarte's menu editor to see if Gnucash appears as an option to be installed in the menu. If not (in fact I don't know) you can make yourself a launcher of Gnucash.

---

### Post by not_yet on 2006-07-18
should be at /usr/bin

also in synaptic if you highlight the program then click on  "properties" at the top, it will tell you where all the files for your app are located

cheers

---

### Post by JShadow on 2006-07-18
Try pressing F2 and typing gnucash into the prompt. If that launches it then you'll just need to make a shortcut on your menus. It went under office by default on my system. The location of the file would be /usr/bin/gnucash

---

### Post by JoWilly on 2006-07-18
Gnucash 2 is much nicer than the older version in the repo, it has a new gtk2 gui.

You can get the ubuntu deb packages on page 10 and 11 of this thread:
[http://ubuntuforums.org/showthread.php?t=127587&page=10](http://ubuntuforums.org/showthread.php?t=127587&page=10)

[http://c.chez.fred.free.fr/gnucash-common_2.0.0-1_all.deb](http://c.chez.fred.free.fr/gnucash-common_2.0.0-1_all.deb)
[http://c.chez.fred.free.fr/gnucash_2.0.0-1_i386.deb](http://c.chez.fred.free.fr/gnucash_2.0.0-1_i386.deb)
[http://c.chez.fred.free.fr/gnucash-docs_1.9.0-1_all.deb](http://c.chez.fred.free.fr/gnucash-docs_1.9.0-1_all.deb)

---

### Post by citylife on 2006-07-18
thanks for your knowladge

---

### Post by reclusivemonkey on 2006-07-18
> **citylife said:**
> thanks for your knowladge

Not forgetting of course (should you lose anything else in the future ;-) )

```

whereis gnucash

```

---

### Post by mjpatey on 2006-07-18
Thanks, everyone!

I found the program, ran it, decided to uninstall and follow the link from JoWilly for the version 2.0 thread.  Installed it from the .deb files, and voila!  Made a shortcut to it on the desktop.

Woohoo!

-Mark

---

