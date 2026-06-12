---
title: "Help with GDM theme"
date: 2009-02-18
forum: General Help
---

### Post by Adrenochrom3 on 2009-02-18
ok so i have been afraid to change my GDM (Login) screen. the last time i did that, my computer wouldn't load the login window. and i had to go threw a bunch of crap to change the login screen back to normal via terminal before login. i think i had to push alt F1 or F2. but either way i had to type in some code, and needless to say it worked. but what im trying to ask isssss...  what do i have to do to change my GDM theme correctly

i had a theme package, stored it im my pictures/background images/GDM theme... and installed the package through the login window preference, and according to the computer i did it correctly. so what should i do to make this work, without having to go threw that crap again?

---

### Post by wildman4god on 2009-02-18
thats the way you should do it, i have run into that problem some times, its a problem with the theme, some themer's for some odd reason can package or make it correclty, my advise is to try another theme. also give me a link to the theme you used and let me see if I can get it to work. also if your theme doesn't work and you get a cli on boot up just log in and type startx and that should get the gui up and running again so you can change the gdm theme back to one that works.

---

### Post by Adrenochrom3 on 2009-02-18
here is the theme i picked, the dark+brown one is the one that i wanted to install.

[http://www.gnome-look.org/content/show.php/nUbuntu+GDM+Logins?content=73883](http://www.gnome-look.org/content/show.php/nUbuntu+GDM+Logins?content=73883)

---

### Post by wildman4god on 2009-02-18
weird I installed it and it worked fine, just try another theme first and see if it'll work, if it works try the theme you want and see what happens if you get the same problem again some thing is seriously wrong with your ubuntu install.

---

### Post by Adrenochrom3 on 2009-02-18
well see thats the thing, im kinda afraid to install it again, in fear that it wont install correctly or what not. and i forgot what commands i was supposed to type in to fix it back to normal if infact it doesnt work. all i remember is that i had to use the terminal before login, and i had to change the GDM theme from there. and i guess the thread got erased, cause i cant find the thread on here that helped me do that. blah... i hope my computer will be ok...

The theme also states: "It is resolution independent the screenshot was taken on a 1440x900 resolution so it could be tight on a 800x600 res and don't even think about having it on a 640x480

so there shouldnt be any problem with the resolution.

---

### Post by wildman4god on 2009-02-18
I have had the whole gdm problem where you get a terminal screen, just type in your username and password and type startx (sudo startx if that didn't work) that got me in to the gui and let me change the theme again. If you really don't wanna risk it then don't try it, its  not the end of the world if you don't have a new login theme, it doesn't matter to me as I just auto login so I never see mine. But I would encourage you to try, thats the only way you will learn to fix things is to break them first. I will try and find the commands so if it breaks agian you can fix it. the only thing I can think of right now that would cause the gdm to goto cli is an incompatible screen resolution, try another theme, there are ones install in the login screen manager try one of those, if it does it again theres some thing wrong with gdm and it needs fixed. wait untill I find the commands.

---

### Post by Adrenochrom3 on 2009-02-18
ok thank you Wildman. ill wait upon your response with the codes.

---

### Post by wildman4god on 2009-02-18
this thread shows how to remove an offending theme (a theme gdm doesn't like) so if you try a new theme and you get problems just do what the thread says:

[http://ubuntuforums.org/showthread.php?t=870982](http://ubuntuforums.org/showthread.php?t=870982)

also if you ever have any problems just pm me and I will help you as much as I can.

---

### Post by Adrenochrom3 on 2009-02-18
ok so i tried this GDM Theme: [http://www.gnome-look.org/content/show.php/MushroomLake?content=93672](http://www.gnome-look.org/content/show.php/MushroomLake?content=93672)     

and it worked fine. but i still havent tried the other theme. but thank you for the info.

---

### Post by wildman4god on 2009-02-19
No problem, let me know when you try the other theme.

---

### Post by BigSilly on 2009-04-05
The nUbuntu GDM theme has just caused me no end of bother on my 64 bit install too. Had to manually remove it from usr/share/gdm/themes in the end. It's odd, because on my 32 bit Ubuntu install it's been absolutely fine! I've gone back to the lovely Arc Colours theme now.

---

