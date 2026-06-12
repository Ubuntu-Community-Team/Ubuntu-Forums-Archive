---
title: "Compiz desktop cylinder inside-out?"
date: 2009-08-03
forum: Desktop Environments
---

### Post by tgeer43 on 2009-08-03
I'm converting from 32-bit jaunty to 64-bit so the install is pretty fresh. I have Compiz Fusion installed and configured just like on my 32-bit install but have two 'slight' anomalies.

My desktop cube deformation is set to 'cylinder' but when I rotate it, my viewpoint is that from the inside of the cylinder looking out! I don't know why this is and can't find a setting to change it so that I'm looking at the cylinder from the outside. I seem to recall a setting somewhere that allowed changing the viewing distance from the cube/cylinder and thought that might be the problem but can't find anything like that now.

Secondly, my desktop wallpaper stubbornly insists on being the same on each desktop instead of 4 different wallpapers. I've made sure to set nautilus _not_ to draw the desktop in gconf.editor. That's all I remember having to do when setting up my 32-bit install and every post I have read seems to confirm this but the only wallpaper I get is the one set in System -> Preferences -> Appearance. I know I've got to be missing something simple, but what?

EDIT - I solved the wallpaper issue. Seems I mistakenly invoked gconf-editor originally with 'sudo' so nautilus was still drawing the desktop when I was not logged in as root. Now if I can just get the inside-out cylinder thing resolved.

Thanks in advance,

tgeer

---

### Post by nhanquy on 2009-08-03
Enable Desktop Cube ->Behaviour->Inside Cube : OFF

---

### Post by tgeer43 on 2009-08-03
> **nhanquy said:**
> Enable Desktop Cube ->Behaviour->Inside Cube : OFF

Ha! I just knew it was going to be something obvious that I overlooked. Thanks so much!

tgeer

---

