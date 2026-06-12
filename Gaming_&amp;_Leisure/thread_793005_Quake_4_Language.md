---
title: "Quake 4 Language"
date: 2008-05-13
forum: Gaming &amp; Leisure
---

### Post by howitzer99 on 2008-05-13
ok i just installed Quake4 on Hardy 8.10 i386 version and when i run the game it is a different language then mine.. i think it is Spanish how do i change this..under linux

---

### Post by JohnSearle on 2008-05-13
> **howitzer99 said:**
> ok i just installed Quake4 on Hardy 8.10 i386 version and when i run the game it is a different language then mine.. i think it is Spanish how do i change this..under linux

I haven't installed Q4, but I would expect that the config file for the game would be a good place to start. Usually the game settings are easily modifiable through it.

- John

---

### Post by situz on 2008-05-13
you need to edit Quake4Config.cfg, search the file for spanish (which i think is set to the default language for some reason) and change it to english. you can find this cfg file here: /home/(yourname)/.quake4/q4base/

btw you need to be root to edit it.. ;)

---

### Post by howitzer99 on 2008-05-13
and how do u become root.. i am a newbie to linux..? :lolflag:

---

### Post by situz on 2008-05-13
type "sudo" before the rest of the command.. for example:
> sudo gedit /home/???/.quake4/q4base/Quake4Config.cfg

obviously you need to replace "???" with your username, and you'll be prompted for root password, this is the same passord as your users login password (usually)

---

### Post by Sockerdrickan on 2008-05-13
You do not need to be root and you should **not** be when you don't need to. The config file is created by the user and can be edited like normal by the user. If not, you have ran Quake IV as root the first time which shouldn't have done, really.

---

### Post by situz on 2008-05-13
well, I followed this guide:
[http://www.linux.com/articles/49600?page=2](http://www.linux.com/articles/49600?page=2)
and after doing so I had the exact same problem as howitzer99, so I did like I told him. 

I think the reason why this happens is because of the installer program you need from id-software to be able to install the game. maybe that installer makes these files owned by root?

if so it should be reported to id-software

---

### Post by howitzer99 on 2008-05-13
hey got it working in english .. i did what situz said to do but .. i just ctrl+h to unhide the .quake4 folder and then right clicked on it and opened in a text editor.. and i didn't have to be root.. thx for the help guys.. 

Ubuntu rocks most of the games i do play run better on ubuntu then on native windows.. lol funny.. but it works well .. thx again for all the help..

:guitar:

---

### Post by Sockerdrickan on 2008-05-14
> **howitzer99 said:**
> hey got it working in english .. i did what situz said to do but .. i just ctrl+h to unhide the .quake4 folder and then right clicked on it and opened in a text editor.. and i didn't have to be root.. thx for the help guys.. 

That's great to hear. Just as I thought.

---

### Post by situz on 2008-05-14
good good =) 

wierd tho, guess I did something wrong when I installed the game :P

it's np tho, I've changed the owner and stuff on my game files.

---

