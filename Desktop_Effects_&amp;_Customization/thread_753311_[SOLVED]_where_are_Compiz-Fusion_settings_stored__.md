---
title: "[SOLVED] where are Compiz-Fusion settings stored?  how can i copy them from one PC to"
date: 2008-04-12
forum: Desktop Effects &amp; Customization
---

### Post by bluepowder7 on 2008-04-12
in the ongoing saga of recovering some info from my laptop's hard drive (machine crapped out, hard drive is intact), i'm going through the process of setting up my desktop machine to be similar to what my laptop was.  i'm also making changes along the way, so not everything is going to be the exact same way.

except compiz-fuzion.  i want that to be set up identically to how it was on my laptop.  since i've got access to the laptop's hard drive, i copied over the entire /(root) and /home directory.  question is - where are all of my compiz-fusion settings stored so that i can copy the folders and files over from the laptop's drive over to the desktop's drive?

i looked in /home/greg/.config/compiz and the file there is small and has next to no content.  i don't want to copy the ENTIRE home folder because i've realized that there's stuff i want to do differently this time around.

---

### Post by tamoneya on 2008-04-12
take a look at /home/greg/.compiz

---

### Post by bluepowder7 on 2008-04-12
> **tamoneya said:**
> take a look at /home/greg/.compiz

unfortunately, i don't seem to have that folder, so maybe it's buried somewhere else?  here's what i do have under /home/greg on the laptop:

(clickable thumbnail)

[[IMG]http://i106.photobucket.com/albums/m244/GregR7/screenshots/th_home_folder.jpg[/IMG]](http://i106.photobucket.com/albums/m244/GregR7/screenshots/home_folder.jpg)

---

### Post by bluepowder7 on 2008-04-12
update - turns out that if i just copy the ~/.gconf/apps/compiz folder structure from my old drive over to the new one and reboot, i get all my old settings back!  i guess it stores the settings in the dozen or so *.xml files that are nested in there.

hopefully, if someone searches for "how to restore or copy my compiz fusion settings from another computer or hard drive", they'll find this and it'll help them.

---

