---
title: "no mouse on games"
date: 2005-05-26
forum: Gaming &amp; Leisure
---

### Post by 1000i1 on 2005-05-26
I've had a lot of problems with xfree86, and after reinstalling it several times now it's working well and the nvidia-glx is working also, everything goes fine except that when I run enemy territory I get no mouse, I see the mouse pointer in the middle of the screen, and I can't move it, The only thing that happens is that the screen rotates when I move the mouse. I have no idea on how to solve this, as I've put the right things on my XF86Config-4 (at least I think so), and when executing et, I haven't seen any problem related with the mouse.

---

### Post by jdodson on 2005-05-26
[QUOTE=1000i1]I've had a lot of problems with xfree86, and after reinstalling it several times now it's working well and the nvidia-glx is working also, everything goes fine except that when I run enemy territory I get no mouse, I see the mouse pointer in the middle of the screen, and I can't move it, The only thing that happens is that the screen rotates when I move the mouse. I have no idea on how to solve this, as I've put the right things on my XF86Config-4 (at least I think so), and when executing et, I haven't seen any problem related with the mouse.[/QUOTE]

if you are using xfree86, then you are running warty and you are posting to the wrong area.  hoary uses xorg.

---

### Post by 1000i1 on 2005-05-26
Well, thanks for the reply but I'm posting in the right place, I'm using hoary and I'm using xfree86, It was easier for me to get it running.

PS: I don't know if it's me but your reply sounds quite rude, man I know lots of people post without reading, but that doesn't mean everybody does it, so please ask before accusing.

---

### Post by equilibrium on 2005-05-26
I remember ages ago there was a problem with a new version of xfree and quake3. So iD Software released quake3 1.32b to replace 1.32, but not sure about any other games.

I think that was to do with the DGA extension in xfree (quake3: in_dgamouse "1")

maybe check you have dga enabled in xf86config.

Section "Module"
```

    SubSection  "extmod"
#     Option    "omit xfree86-dga"   # don't initialise the DGA extension
      Option    "xfree86-dga"   # initialise the DGA extension
    EndSubSection

```

Otherwise I'm not too sure :) as I've not had any other problems. What games are you having problems with?

---

### Post by 1000i1 on 2005-05-27
Well, actually I haven't tried more games, and what's important and I forgot to say is that before reinstalling nvidia drivers and xfree86, enemy territory was working perfectly. My config file says nothing about dga, maybe I should add this lines.

---

### Post by 1000i1 on 2005-05-30
Ok, now it works, I had reinstalled so many times xfree86 that I forgot to read everything on my new configuration, there was a problem under the "Device" and "protocol" sections, now everything works fine.

---

