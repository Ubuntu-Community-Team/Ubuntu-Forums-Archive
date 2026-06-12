---
title: "Wolfenstein:et doesnt work!!!"
date: 2005-06-11
forum: Gaming &amp; Leisure
---

### Post by fireedo on 2005-06-11
I have installed wolfenstein:ET and when I try to run the game is just show me a blank screen.....I'm waiting...waiting....waiting....until 5 minutes and there is nothing happen.....so what's wrong?

I have installed ATI driver and tested well.....fgl_glxgears+glxgears shows reasonable score and glxinfo is ok too.....so what's the problem?

---

### Post by felipe on 2005-06-12
i installed et 2.60 on hoary, so far no problem (nvidia video card)

tell us which version of et, and if you have similar problems with other games

---

### Post by kiddo on 2005-06-12
Same here, works flawlessly with NVidia :) maybe you could try launching it from a terminal so you can get the output

---

### Post by fireedo on 2005-06-12
[QUOTE=kiddo]Same here, works flawlessly with NVidia :) maybe you could try launching it from a terminal so you can get the output[/QUOTE]
 ok now my wolfenstein is work.....but no sound.....and I have a little silly questions....can I play single player with wolfenstein:ET? because I have a bad internet connection

---

### Post by felipe on 2005-06-12
only multiplayer, sorry

as for the sound... do this:

```

sudo echo "et.x86 0 0 direct" | sudo tee -a /proc/asound/card0/pcm0p/oss

```

---

### Post by fsman on 2005-06-12
[QUOTE=felipe]only multiplayer, sorry

as for the sound... do this:

```

sudo echo "et.x86 0 0 direct" | sudo tee -a /proc/asound/card0/pcm0p/oss

```[/QUOTE]


Do I have to do this each time I boot? When I reboot my sound disappears - a real pain.

Is their a perminant solution?

---

### Post by felipe on 2005-06-28
[QUOTE=fsman]Do I have to do this each time I boot? When I reboot my sound disappears - a real pain.

Is their a perminant solution?[/QUOTE]
 sorry but, yes you have to do it after each reboot. no perm solution

you could put those commands in a custom boot script, but that's likely to cause minor annoyances, so... your choice

---

