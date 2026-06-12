---
title: "MAME issue...."
date: 2008-10-28
forum: Gaming &amp; Leisure
---

### Post by Lee83 on 2008-10-28
after installing gxmame-common and the front end via package manager i have a problem when coming to load roms..do the roms have to be in the mame/roms/ directory or any one i choose,i notice there is an option to change the path of the roms directory but on doin this there is still no change,of the 5 or so roms ive tried non work and come back with a display error LIRC disabled....any help appreciated,thanks

---

### Post by FranMichaels on 2008-10-28
Try sdlmame instead, not sure if your chosen front-end is supported, but sdlmame is up to date with the official mame, and rocks hard.

---

### Post by Lee83 on 2008-10-30
ive installed sdlmame and the sdlmame tools package (not sure if needed but hey?) do i also install the xmame-common package and xmame as the front end?? what front end do you use,im running gnome desktop if that makes a difference..

---

### Post by disturbedite on 2008-10-30
> **Lee83 said:**
> ive installed sdlmame and the sdlmame tools package (not sure if needed but hey?) do i also install the xmame-common package and xmame as the front end?? what front end do you use,im running gnome desktop if that makes a difference..
i think you've got a few things confused.

xmame is an emulator, so to speak. it is far outdated and shouldn't be used.

sdlmame is a newer mame emulator (port). use it.

gxmame/kxmame are frontends. gxmame is for use with xmame. kxmame is for use with xmame OR sdlmame.

i recommend kxmame with sdlmame. kxmame has many improvements over gxmame.

but don't install the kxmame package from the ubuntu repos. install doktorseven's kxmame package. (the older package of kxmame in the ubuntu repos is outdated and doesn't support sdlmame).

---

### Post by Lee83 on 2008-10-30
ok i will try that,and yes i am confused,been ubuntu user for about 6 months and still learning :)

ok i downloaded the package from the d7 website and installed sdlmame via repo but there is no icon in game folder to start app,or is there a bit more to it than just installing those two packages??

---

### Post by wingnux on 2008-10-30
Always get the latest version of sdlmame from here: [http://wallyweek.altervista.org/](http://wallyweek.altervista.org/)

Change the settings by typing this command on the terminal window: sudo gedit /etc/sdlmame/mame.ini

Run "sdlmame" (it has a built-in rom browser), type the 1st letter of the game you want to play to sort the listing by that letter.

The tab key acts as an in-game menu.

---

### Post by Lee83 on 2008-10-30
ok i got mame to work :) sorted although the marvel vs capcom i wanted to try didnt have all files but im undeterred,will try a few more i think,thanks for all your help..

---

