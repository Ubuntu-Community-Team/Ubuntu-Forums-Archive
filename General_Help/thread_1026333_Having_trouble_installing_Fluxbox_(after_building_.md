---
title: "Having trouble installing Fluxbox (after building from source)"
date: 2008-12-31
forum: General Help
---

### Post by The Notorious VLG on 2008-12-31
I'm running Ubuntu 8.10 (AMD 64) and I'm trying to get Fluxbox working. I got the source files and built the package successfully and installed it (and the package manager, for example, recognizes that it's installed) but I'm unable to access Fluxbox after restarting. I'm trying to install the latest version, 1.1.0, and it was installed into /usr/local/bin and /usr/local/share/fluxbox. I've edited my .xinitrc file as indicated here: [http://fluxbox-wiki.org/index.php?title=Start_fluxbox_from_the_command_line](http://fluxbox-wiki.org/index.php?title=Start_fluxbox_from_the_command_line) (the first option). It still doesn't seem to work though.

---

### Post by The Notorious VLG on 2008-12-31
Sorry, it's Fluxbox 1.1.1, not 1.1.0.

---

### Post by The Notorious VLG on 2008-12-31
Also, by downgrading to 1.0.0 it works. If I try to install 1.1.1 after that it doesn't work anymore though.

---

### Post by RedSquirrel on 2009-01-01
(1) If you have an old ~/.fluxbox directory lying around, I would recommend renaming it:

```
mv ~/.fluxbox ~/.fluxbox.old
```The newer versions of Fluxbox use some new settings in the configuration files, and it's probably best to have a clean set of files to start with. The new set of files will be generated automatically the first time you run the new Fluxbox.



(2) How do you start X? Do you run a display manager (e.g., gdm) or do you login on the console and run 'startx'?

If you're using gdm, you'll need to create a /usr/share/xsessions/fluxbox.desktop file and have the "exec" lines in that file run the new **startfluxbox** script stored in /usr/local/bin.


With regard to the configuration files under ~/.fluxbox, part of the problem may be your old **~/.fluxbox/startup** file. If you have an old ~/.fluxbox directory lying around, it's very likely that the old **~/.fluxbox/startup** file runs /usr/bin/fluxbox. You could change that to just:

```
fluxbox
```or specify the absolute path like this:

```
/usr/local/bin/fluxbox
```**but** it's probably better to just start with a fresh ~/.fluxbox directory as I mentioned in point (1) above. ;)

---

