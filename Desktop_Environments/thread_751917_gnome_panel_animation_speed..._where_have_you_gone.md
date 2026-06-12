---
title: "gnome panel animation speed... where have you gone?"
date: 2008-04-11
forum: Desktop Environments
---

### Post by Mitch on 2008-04-11
How do I speed up the animation speed of the gnome panel (as it hides and unhides)?  Seems like editing panel_animation_speed in gconf-editor should do the trick.  However gconf-editor says it's deprecated and changing this setting doesn't seem to do anything.  

I'm running Hardy.

---

### Post by Zogg on 2008-04-23
How come nobody replied?

Schema says Now it should be "animation_speed", however, i get a warning that schema for such key doesnt exist.

So, how do we set animation speed?

---

### Post by mnichau on 2008-04-24
Same problem here. Just upgraded to Hardy and it seems that the menus are slower. For now I just switched the animation off entirely for panels:

for that, e.g. run this in the terminal:
$> gconf-editor

Then go to the key: /apps/panel/toplevels

You'll see your panels listed inside. For each of them you can clear the option "enable_animations".

Yes, it is not exactly what I was searching for either. What I really want to do is to keep the animations but increase their speed. For now, however, this will do as a temporary fix for me.

I hope someone will post the actual way of speeding up the panel animation speed.

Cheers!

---

### Post by 3ntity on 2008-04-27
> **mnichau said:**
> Same problem here. Just upgraded to Hardy and it seems that the menus are slower. For now I just switched the animation off entirely for panels:
...Thx :)
I like the panel hiding instantly; together with auto_hide_size 0 it's just how i like it :)

Before arriving in this thread i'd tried changing panel_animation_speed but that obviously hadn't helped.

---

### Post by Chbuntu on 2008-05-01
> **3ntity said:**
> Thx :)
I like the panel hiding instantly; together with auto_hide_size 0 it's just how i like it :)

Before arriving in this thread i'd tried changing panel_animation_speed but that obviously hadn't helped.

Hello. In hardy, I was able to adjust the auto_hide_size to 0 but my attempts to change the hide_delay and unhide_delay went unsuccessful. I changed the keys from 500 to 50 as I did in gutsy.  Any ideas?

---

