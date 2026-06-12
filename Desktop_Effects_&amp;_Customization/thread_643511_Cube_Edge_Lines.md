---
title: "Cube Edge Lines"
date: 2007-12-17
forum: Desktop Effects &amp; Customization
---

### Post by alejandro.mc on 2007-12-17
Hey everyone, my cube has this horrible edges that shine and are really disturbing, probably easy to deal with them but i obviously don't know how, i'll attach a picture. Maybe someone has some ideas..

Thanks a lot in advance!

---

### Post by alejandro.mc on 2007-12-17
Someone? Over the rainbow, or underneath, both will do..

Sorry about that its too late in Buenos Aires and I sat for many exams this week =)

Bye

---

### Post by FuturePilot on 2007-12-17
I'm not sure but it might be the wallpaper. See if changing it does anything.

---

### Post by alejandro.mc on 2007-12-18
It's not the wallpaper because it does it also in the bottom. Besides I tried other wallpapers. Thanks anyway. Any other ideas?

Alejandro

---

### Post by alejandro.mc on 2007-12-19
Anyone?

THX

---

### Post by rainwalker on 2007-12-20
In CCSM, did you turn on mipmaps for the desktop cube?

---

### Post by hhhhhx on 2007-12-20
are u using beryl or compiz?

---

### Post by alejandro.mc on 2007-12-20
Isnt Compiz and Beryl all together now? I have Compiz Fusion. The mipmaps its turned on. 

Thanks for replying, anyone else? maybe i just have to reinstall all ubuntu again..

Bye!

---

### Post by rainwalker on 2007-12-20
What do you have set for Texture Filter? It's under the "Display Settings" tab in General Options

---

### Post by tomauty on 2007-12-20
Regardless of the filter, this will happen to anyone, it just depends on how contrasted the colors are that will make it more or less noticeable. This is due to the limit of how much antialiasing can really happen while still making compiz fusion usable.

If you use an nvidia card and use the normal drivers, you can type in the terminal "nvidia-settings" and change the antialiasing settings. Just a thought.

---

### Post by hhhhhx on 2007-12-20
I actualy remember this happening in beryl, I got rid of it, by setting some resoloution to max, With my current compiz fusion i changed all of that once i started my system, this proboble doesent help much but if you set resoloutions to the max it should help:confused:

---

### Post by []Milo on 2008-01-12
Hi Alejandro, 

Its probably antialiasing.  Compiz does some antialiasing and you can change the quality by 
 - opening the Compiz Settings Manager (System --> Preferences -->Advanced Desktop Effects Settings) 
 - select "General Settings"
 - open the "Display Settings" tab 
 - change the Texture Filter drop down to "Best"

If you don't have the settings manager installed (its not by default i believe)

```
sudo apt-get install compizconfig-settings-manager
```


there's also a discussion here:
[http://ubuntuforums.org/showthread.php?t=646356&highlight=antialiasing]("http://ubuntuforums.org/showthread.php?t=646356&highlight=antialiasing")

---

