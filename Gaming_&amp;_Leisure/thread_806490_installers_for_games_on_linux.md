---
title: "installers for games on linux"
date: 2008-05-25
forum: Gaming &amp; Leisure
---

### Post by Cap'n Skyler on 2008-05-25
Loki has made linux installers for unreal tournament for a long time.
can some one give me the short version of what is done/how it's done to make an installer?
i see unreal tournament 2004 and have played both in linux and windows xp.
both have their files in their respective directories.
obviously there is more than just making the files in a given directory and then playing the game.
 just curious is all,i have no clue how the installer works.and i want to know

:guitar:

---

### Post by Cappy on 2008-05-25
The 'loki installer' generating tools are here:
[http://icculus.org/loki_setup/](http://icculus.org/loki_setup/)

If you want to see how it works, I would download the ET:QW (Quake Wars) demo since it is newer, if you wanted to look.

```
./loki_installer.run --target new_loki_dir
```
and the script is in setup.sh

or you can just nano the loki_installer and look at it that way. It's just a shell script with the binaries packed behind it.

---

### Post by Cap'n Skyler on 2008-05-25
> **Cappy said:**
> The 'loki installer' generating tools are here:
[http://icculus.org/loki_setup/](http://icculus.org/loki_setup/)

If you want to see how it works, I would download the ET:QW (Quake Wars) demo since it is newer, if you wanted to look.

```
./loki_installer.run --target new_loki_dir
```
and the script is in setup.sh

or you can just nano the loki_installer and look at it that way. It's just a shell script with the binaries packed behind it.
so are you possibly saying,that the game makers and the lawyers are the ones behind the lack of linux game support?OMG!!!
meanwhile,i'll go check out the loki installer :P
thnaks a billion!!

---

### Post by cogadh on 2008-05-25
Actually, the installer has very little to do with whether or not a game will work on Linux. It has everything to do with the graphics and sound systems used (Windows only systems like DirectX and EAX versus open standards like OpenGL, OpenAL and SDL) and whether or not a Linux-compatible executable binary has been created for the game. Having an installer that puts everything in the right places is useless if the game is DirectX and has only an EXE for a binary (unless you make the installer to work with Wine... maybe).

---

