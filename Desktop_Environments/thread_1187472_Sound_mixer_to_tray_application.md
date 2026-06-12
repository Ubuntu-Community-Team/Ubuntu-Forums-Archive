---
title: "Sound mixer to tray application?"
date: 2009-06-14
forum: Desktop Environments
---

### Post by del_diablo on 2009-06-14
Installed Openbox then threw in Docker. Now i am lacking just 1 thing: A simpel mixer applet........... I have tried absvolume, but it failed to adjust volume.

---

### Post by leef on 2009-06-14
I just can't seem to find a gtk mixer applet that works in window managers either I ended up using kmix instead :(

edit;

actually it seems that absvolume can be hacked to work all you have to do is find all;

```
SOUND_MIXER_PCM
```

and replace it with the following;

```
SOUND_MIXER_VOLUME
```

in these files;

```
src/main.c
src/callbacks.c
src/actions.c
```

compile it and make install again. finally a gtk mixer applet :) thanks for making this topic.

Here is an archive with the changes already made

---

### Post by del_diablo on 2009-06-15
Your welcome and thanks :P

---

