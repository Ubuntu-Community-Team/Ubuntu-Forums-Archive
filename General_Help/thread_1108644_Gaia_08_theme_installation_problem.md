---
title: "Gaia 08 theme installation problem"
date: 2009-03-27
forum: General Help
---

### Post by andpie on 2009-03-27
Alright so i was looking around deviant art yesterday and found this:

[http://iamfuss.deviantart.com/art/Upgrade-to-Jaunty-Jackolope-115782315](http://iamfuss.deviantart.com/art/Upgrade-to-Jaunty-Jackolope-115782315)

I really liked it and decided to copy it, heres what ive got so far:

What Works:

Gaia 08 Emerald Theme

Wallpaper( real hard lol )

Screenlets ( easiest part )

What Doesnt:

Gaia 08 Gtk theme (made it a tar.gz file and get error message: cant move directory over directory.)

Gaia 08 Icons (downloaded it, tried compiling it but doesnt work)

Gaia 08 Pidgin Status Icons


Please Help

---

### Post by andpie on 2009-03-28
still no answer?

---

### Post by transgress on 2009-03-28
why are you making the theme a .tar.gz file? Extract it, and copy it manually to your .themes directory. There should be nothing to compile with the icons. Icons are images under normal circumstances. Just move them to the .icons folder.

Haven't changed pidgin status icons in a while or ever, but I did a minimal google search of "changing pidgin status icons" and got this command:
as root run 
cp -r * /usr/share/pixmaps/pidgin/*
in the directory of icons that you want to change it to. Because this appears to be overwriting the pidgin ones you may want to back up the originals first.

---

