---
title: "No title bar with desktop effects"
date: 2007-05-26
forum: Desktop Effects &amp; Customization
---

### Post by joshaude on 2007-05-26
I turned on the desktop effects in Feisty Fawn and the title bars on all my windows disappeared. Also, it turns my number of workspaces to one and doesn't do the cube thing at all. My nVidia stuff is already configured. Really this is the only problem I'm having. Any help would be greatly appreciated. Also, this question is not related to Beryl at all considering I don't have it installed.

---

### Post by drummingpariah on 2007-05-26
> **joshaude said:**
> I turned on the desktop effects in Feisty Fawn and the title bars on all my windows disappeared. Also, it turns my number of workspaces to one and doesn't do the cube thing at all. My nVidia stuff is already configured. Really this is the only problem I'm having. Any help would be greatly appreciated. Also, this question is not related to Beryl at all considering I don't have it installed.

Desktop effects are a feature of Beryl.  Are you certain you don't have it installed?

---

### Post by joshaude on 2007-05-26
Feisty Fawn comes with desktop effects. You don't need Beryl. It's under System->Preferences->Desktop Effects

---

### Post by drummingpariah on 2007-05-26
Actually, it's a Compiz (Beryl) feature that's included with Ubuntu, regardless of whether you're using gnome or kde.  It's likely that one of the recent updates has messed with beryl (I'm working on exactly what it was currently, I believe it was an update to Xorg).  Do you happen to have an nVidia card?

---

### Post by meneer on 2007-05-26
The same happened to my system. Update killed xorg config and after runnig dpkg rconf I managed to use nv driver in stead of the nvidia driver.
Using automatix I installed the nvidia driver and then the title bars disappeared.

I did have compiz activated.

Any clue?

---

### Post by drummingpariah on 2007-05-26
narrowed it down.  Seems to be something that emerald depended on that got updated.  use synaptic to remove emerald completely, then use it again to add it back.  that should re-register the new dependencies and you should be back on your feet.  hope it helps!

---

### Post by evolutionx on 2007-05-26
I noticed the same issue when logging into Gnome after setting up Beryl. The windows were there but they had no borders and could not move them.

The following command fixed it up however;

sudo nvidia-xconfig --add-argb-glx-visuals

Taken from [http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html)

Hope this helps!

---

