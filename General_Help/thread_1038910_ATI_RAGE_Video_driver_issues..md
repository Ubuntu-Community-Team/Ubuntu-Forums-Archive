---
title: "ATI RAGE Video driver issues."
date: 2009-01-14
forum: General Help
---

### Post by Famicommander on 2009-01-14
I asked for help in Absolute Beginner Talk, and three days later I'm not much better off than I was in the first place.

Anyway, I'm trying to install the correct video card drivers for my ancient ATI RAGE 128 Pro graphics card with 32MB of on board RAM. I am mostly trying to get it going well enough to play Open Arena. Here is what happens when I try:
```
jason@jason-desktop:~$ openarena
ioq3+oa 1.35 linux-i386 Sep 10 2008
----- FS_Startup -----
Current search path:
/home/jason/.openarena/baseoa
/usr/share/games/openarena/baseoa/pak7-patch.pk3 (12 files)
/usr/share/games/openarena/baseoa/pak6-misc.pk3 (204 files)
/usr/share/games/openarena/baseoa/pak5-TA.pk3 (15 files)
/usr/share/games/openarena/baseoa/pak4-textures.pk3 (1720 files)
/usr/share/games/openarena/baseoa/pak3-music.pk3 (1 files)
/usr/share/games/openarena/baseoa/pak2-players.pk3 (610 files)
/usr/share/games/openarena/baseoa/pak2-players-mature.pk3 (234 files)
/usr/share/games/openarena/baseoa/pak1-maps.pk3 (89 files)
/usr/share/games/openarena/baseoa/pak0.pk3 (988 files)
/usr/share/games/openarena/baseoa

----------------------
3873 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
SDL_Init( SDL_INIT_VIDEO )... OK
Initializing OpenGL display
Estimated display aspect: 1.250
...setting mode 0: 320 240
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  11
  Current serial number in output stream:  11
jason@jason-desktop:~$ 

```

I am still relatively new and I don't quite know what any of that means, or where my problem lies.

Another issue I have is when I watch DVDs. I can see the refresh lines unless I set it to deinterlace->mean in VLC. I suspect it is related to the above issue.

I know for a fact that this card is capable of playing full-screen DVDs and playing this game competently, because I did it before I upgraded to Inrepid Ibex. It was fine in Gutsy and Hardy. But I did a completely fresh install of Intrepid, and have had no such luck.

Any help would be awesome/

---

### Post by Famicommander on 2009-01-14
How silly of me; I should have mentioned this earlier. This is the command that someone in Beginner Talk told me to run to install the drivers:
```
sudo apt-get install libgl1-mesa-dri xlibmesa-gl xlibmesa-glu mesa-utils libgl1-mesa-dri libgl1-mesa-glx
```

And then I input this:
```
glxinfo | grep "direct rendering"
```

Which gave me this:
```
jason@jason-desktop:~$ glxinfo | grep "direct rendering"
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
jason@jason-desktop:~$
```

I hope that helps shed more light on the situation.

---

### Post by Famicommander on 2009-01-14
Help?

---

### Post by Bablefish on 2009-01-14
I admit fully I have had problems with ATI drivers on Ubuntu one so bad it crashed my video drivers...so be warned. You may have to reinstall your OS if that happens to you.

---

### Post by Famicommander on 2009-01-14
I'm not too worried about that. There is nothing on my hard drive that cannot be replaced.

---

### Post by Famicommander on 2009-01-16
What's a guy got to do to get some video card help around here? Show a little leg?

---

