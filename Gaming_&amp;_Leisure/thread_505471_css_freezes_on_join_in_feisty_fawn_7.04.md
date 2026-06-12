---
title: "css freezes on join in feisty fawn 7.04"
date: 2007-07-20
forum: Gaming &amp; Leisure
---

### Post by Zexter on 2007-07-20
i installed my ati driver. when i rebooted it said i was using restricted hardware, but i check and its using my ati driver.

now, when i launch counter strike source, it tells me my video hardware is out of date, but i clicked continue anyway.

it loads up fine, i can see all the txt perfectly (i put the tahoma.tff in the correct directory)

but right when i join a server it freezes. i can move my mouse, but thats it. 

can someone please help me out here please.
i NEED my cs:s  :P

edit: i know i have the right driver....

zexter@zexter-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8 )

---

### Post by BlahMan_of.Doom on 2007-07-20
Go to your terminal, and type ```
glxinfo | grep direct
```
and then paste the output to us.

EDIT: You're using a Radeon Xpress? So that's a laptop? Are you sure that CS will even run on Windows??

---

### Post by Zexter on 2007-07-20
zexter@zexter-desktop:~$ glxinfo | grep direct
direct rendering: Yes

---

### Post by Zexter on 2007-07-20
no im not on a laptop. i have an e-machine. its my integraded graphics. but source runs flawlessly on windows

---

### Post by BlahMan_of.Doom on 2007-07-20
Alright try this.

```
wine ~/.wine/drive_c/Program\ Files/Steam/steam.exe -applaunch 240
```

Don't worry about WINEDEBUG="fixme-all". Okay, that should launch CS:S. Now, when it crashes, post the output of the terminal here. You can also try adding "-dxlevel 70", "-dxlevel 81" or "-dxlevel 90". That changes what version of DirectX is used to play.

---

### Post by graigsmith on 2007-07-20
it's probably the ati drivers crashing, and not the game.  i havent had any good luck with ati's drivers.

---

### Post by Zexter on 2007-07-20
> **BlahMan_of.Doom said:**
> Alright try this.

```
wine ~/.wine/drive_c/Program\ Files/Steam/steam.exe -applaunch 240
```

Don't worry about WINEDEBUG="fixme-all". Okay, that should launch CS:S. Now, when it crashes, post the output of the terminal here. You can also try adding "-dxlevel 70", "-dxlevel 81" or "-dxlevel 90". That changes what version of DirectX is used to play.

i get a fatal error when i run that code. it tries to load steam, then it says could not load module "bin/vgui2.dll"

also, css opens fine... it freezes once i join a server. itll connect and  everything, then the second i see the map and the servers welcome page, it freezes.

---

### Post by Zexter on 2007-07-21
bump

---

### Post by Zexter on 2007-07-21
> **BlahMan_of.Doom said:**
> Alright try this.
 You can also try adding "-dxlevel 70", "-dxlevel 81" or "-dxlevel 90". That changes what version of DirectX is used to play.

no one is sayin anything. so ill try that, but how do i do it

---

### Post by Zexter on 2007-07-22
bump

---

### Post by BlahMan_of.Doom on 2007-07-22
Um okay. Go to your steam folder in terminal. Then type
```
wine Steam.exe -dxlevel XX
```

Replace XX with 70, 81 or 90. start with 70 and 81.

---

### Post by Zexter on 2007-07-22
that directory exists... but when i get to driv_c and i try to "CD" into /Program Files/

it says theres no such directory, but i know there is because i can see it in the file browser

ive tried it like 10 times.... i know it not a spelling error.

can someone please help me out ASAP

---

### Post by Zexter on 2007-07-23
Bump

---

### Post by jacob01 on 2007-07-23
you cand cd into that directory because it thinks the space it the end of the director to fix it put a \ after program

so it looks like this 
cd /home/jacob/.wine/drive_c/Program\ Files/Steam


this works for when changing directoy when there is a space in a directory name

---

### Post by Zexter on 2007-07-25
still the same problem no matter if i use 70, 81, or 90

it still freezes when i join the game

im still getting the warning my video hardware is out of fate but my drivers are installed, i checked.

---

### Post by jacob01 on 2007-07-31
i have the same problem
but have been unable to get any one to help me people keep telling me to go to different websites and use irc chats which i fialy got working then they tell me somthing i already know

---

### Post by jacob01 on 2007-08-18
did you get it fixed?

---

