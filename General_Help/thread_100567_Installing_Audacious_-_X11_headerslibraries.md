---
title: "Installing Audacious - X11 headers/libraries"
date: 2005-12-07
forum: General Help
---

### Post by filipenetto on 2005-12-07
Hi guys,

I'm installing a player (Audacious), and I'm having problems during the installation. See:

[INDENT][COLOR="Gray"]checking for X... no[/INDENT][INDENT]configure: error: Cannot find X11 headers/libraries[/COLOR][/INDENT]
Somebody know what is this ?

Tks !!!

---

### Post by Joe_CoT on 2005-12-07
you need the dev pack for xorg to install it (ie the xorg headers)

```
sudo apt-get install x11proto-core-dev
```

should do the trick

---

### Post by filipenetto on 2005-12-12
ohhh god ..... didn't works. The error continues.

Any other suggestion ? :???: 

Tks !

---

### Post by nenolod on 2005-12-13
The Audacious FAQ handles this question fairly well.

For a fully functional Audacious install, you will need:
xlibs-dev
libgtk2.0-dev
libglade2-dev
libmodplug-dev
libasound-dev
libogg-dev
libvorbis-dev
liblircclient-dev
libesd0-dev
libsdl-dev
libid3-3.8.3-dev
libflac-dev
liboggflac-dev
libsndfile1-dev

Good luck. :)

---

### Post by filipenetto on 2005-12-13
Ok, I will test when I will be in my house.

Thanks !

---

### Post by filipenetto on 2005-12-14
Hi nenolod,

This procedure works, and he complete the installation, but, I can't execute the program. I try to execute "audacious" in the terminal, and, looking into the Readme file, I found a "beep-media-player" command, but he doesn't work too.

You know how execute them ? 

Thanks !!

---

### Post by filipenetto on 2005-12-15
So, nobody know this ?

:(

Please, help-me ......

---

