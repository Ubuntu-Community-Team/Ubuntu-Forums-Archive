---
title: "SDLMAME: Copying of ROM files"
date: 2008-05-17
forum: Gaming &amp; Leisure
---

### Post by Ronni Joensen on 2008-05-17
Having installed SDLMAME and SDLMAME-tools via Synaptic Package Manager, can anyone instruct me where to copy the ROM files? It seems I get a "permission denied" when I use the destination

```
/usr/local/share/games/sdlmame/roms
```

and since I'm not the "owner" of this library, I can't change the permission settings.

Thanks for any help.

---

### Post by DoktorSeven on 2008-05-17
You can place the ROMs anywhere you want; just edit the configuration file /etc/sdlmame/mame.ini to point to your ROM directory (you need to edit it as root, so do **gksudo gedit /etc/sdlmame/mame.ini** ).

---

