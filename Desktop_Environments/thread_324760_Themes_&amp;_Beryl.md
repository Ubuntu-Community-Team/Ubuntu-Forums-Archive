---
title: "Themes &amp; Beryl"
date: 2006-12-24
forum: Desktop Environments
---

### Post by quark_77 on 2006-12-24
Hello All,

I recently made the brave move from windows to linux and have finally succeeded in setting up Beryl & Xgl (I have an ATI card) so I can have a fantastic looking desktop.

The windows are now decorated, however, I would like to know how I get the controls themed under emerald? From what I can see of the screenshots the controls are themed, but perhaps this is just a mistake.

I have attached a screenshot of myself writing this to show you what I mean... The window borders are decorated but the controls aren't!

Any help would be much appreciated, thanks in advance!

---

### Post by _simon_ on 2006-12-24
Beryl, or rather Emerald only themes the windows.

You need to use gtk2 themes for everything else via System -> Preferences -> Theme

[http://www.gnome-look.org/index.php?xcontentmode=100&PHPSESSID=db54db3b378caa1f64ee7a6bd63cb0ce](http://www.gnome-look.org/index.php?xcontentmode=100&PHPSESSID=db54db3b378caa1f64ee7a6bd63cb0ce)

Just download and then drag and drop into the Theme Preferences window. The same with the icon packs.

This is Dark Blue Emerald Theme with ClearlooksWhiteNoCairo GTK2 (with cutom handles) and SNOWISH-1.0 Icons. The panels are custom.

[[IMG]http://i31.photobucket.com/albums/c358/Beowulf1976/SIMON/th_Example.jpg[/IMG]](http://i31.photobucket.com/albums/c358/Beowulf1976/SIMON/Example.jpg)

---

### Post by quark_77 on 2006-12-24
Hi Simon,

No joy I'm afraid, I have opened System > Preferences > Themes and changing theme doesn't do anything. I have set Beryl to run under its own Xgl session using a startup script, if I revert back to GNOME I can change the GTK2 themes, but not with Beryl running!

Any ideas?

Thanks again!

---

### Post by _simon_ on 2006-12-24
I'm afraid I don't know, can't find anything on this problem. 

If I come across anything I'll post.

---

### Post by _davidh on 2006-12-24
Hi quark_77.

I had the same problem some time ago, see if this thread helps you: [http://ubuntuforums.org/showthread.php?t=309984](http://ubuntuforums.org/showthread.php?t=309984)

---

### Post by quark_77 on 2006-12-24
I found my problem, gnome-settings-daemon had been killed by the beryl install. I re-added it to the session startup system>preferences>sessions>startup programs, ctrl+alt+backspace just to be sure, logged back in and that sorted it! GTK2 themes are working!

Thanks for your help everyone!

---

