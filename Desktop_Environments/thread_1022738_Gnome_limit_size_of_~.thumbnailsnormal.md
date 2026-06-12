---
title: "Gnome limit size of ~/.thumbnails/normal"
date: 2008-12-27
forum: Desktop Environments
---

### Post by graysky on 2008-12-27
Is there a way I can limit the size of my ~/.thumbnails/normal within Gnome? I know I can use a cron job to wipe it, but I'd much rather keep it limited to say 10 megs. I poked around in Nautilus preferences, but found nothing.

---

### Post by gettinoriginal on 2008-12-27
Install Configuration Editor via Synaptic.  After installation:
Applications > System Tools > Configuration Editor > Desktop > gnome > thumbnail, set parameters there.  :P

---

### Post by graysky on 2008-12-27
Thanks for the suggestion... I did find an option for desktop>thumbnailers to either enable or disable the generation of thumbnails for various file types, nothing about limiting the size of a given directory.

---

### Post by gettinoriginal on 2008-12-27
Right above thumbnailers should be thumbnail cache, that is where you set the limit.

---

