---
title: "Installing and running apps using wine"
date: 2006-01-10
forum: General Help
---

### Post by naturalhl2 on 2006-01-10
Hey I finally got Wine working right and I can run some windows apps like steam etc..
well when I went to install steam lets say I sent it to its default folder which is sort of like this C:/windows/program folder/steam etc.. well it ran after I installed it but how do I get back to it after I close it out? I went into the terminal and tried this meathod..
Wine steam.exe Says something isent found?? So what do I do about folder locations with other applications I may try to run and how will I run them..?

---

### Post by Zillion on 2006-01-11
How did you get Wine working? I read different posts on the forum but I still dont understand how to install it, cuz if you install Winsetupk from Synaptic, it uninstalls Wine??

So lets do 2 simple questions :

1. How do I install Wine?
2. How can I install a Windows application?

tx

---

### Post by Viro on 2006-01-11
You just need to install wine. Do not download and install winesetup. Instead, use the supplied tool called winecfg, which is far better. Just use the defaults and it should create a .wine directory for you that works quite well.

To install a windows application, just do wine *program installer*.exe. To access your app again, you need to find your C: drive, and that is located at ~/.wine/drive_c/

Now for example if you installed steam in c:\Program Files\Steam\ and you want to run it using wine, you need to type the following into the terminal
```

cd .wine/drive_c/Program\ Files/Steam
wine steam.exe

```

---

### Post by redmansk8 on 2006-01-11
Hello:

  I installed wine and since then I have been trying to load different windows programs I got IE6 to install and open correctly but on other programs I get errors installing them or get errors try to open the programs after install. one error I got on several programs  was libGL error then its say something about 3d driver not found

---

### Post by akiro.yamamoto on 2006-01-11
redmansk8:
Do you have a 3d card with the drivers installed?
Give us some more details.

---

### Post by redmansk8 on 2006-01-11
I have a SIS 630-730 AGP video which is a 3d card I have not installed any drivers other that what ubuntu installed during setup

here is a screen shot of the error I get when you get error the program begins to open but never finishes opening

rik@ubuntu:~$ wine "C:\PROG~FBU\Cooledit\coolpro.exe"
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering
fixme:process:SetProcessWorkingSetSize (0xffffffff,8388608,16777216): stub - harmless

---

### Post by naturalhl2 on 2006-01-11
Ok inorder for me to run Steam right I need an active x controller how do I go about getting AND USING

---

### Post by naturalhl2 on 2006-01-13
Bump

---

### Post by redmansk8 on 2006-01-14
Hello 

I got wine to install MS Access and MS Front Page From the office XP disc access opens fine I create a Database and every thing. Front Page opens then a front page windows comes open and says front page has an error and needs to close. I was wondering has anyone else installed front page XP and if they had that error and what they did to fix it.  I like Ubuntu  but it would be nice to get front page working cause I use front page to manage my web sites.

---

