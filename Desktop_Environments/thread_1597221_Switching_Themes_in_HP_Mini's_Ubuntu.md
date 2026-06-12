---
title: "Switching Themes in HP Mini's Ubuntu"
date: 2010-10-15
forum: Desktop Environments
---

### Post by jczeroman on 2010-10-15
All,

I readily admit I know next to nothing about Linux - so I am pleading mercy here.

My HP Mini 1000 had to be factory reset and that means no more Windows XP on the machine until I can figure out how to install it via USB flash. The machine comes with, from what I can figure out, a modified version of ubuntu.

What I wanted to do was to change away from this iphone-like default GUI but I cannot find any menu options to change the theme (System > Preferences > Theme) There is nothing like that anywhere on the computer as far as I can tell. Nothing. The OS help file even says to go to these menus, but they do not exist.

Does anyone have any knowledge that may be helpful here? Am I going to have to install a completely fresh OS? Surely there is a way to switch themes...

---

### Post by Peter09 on 2010-10-15
Mmm depends what is installed on your machine. At the login window .... before you enter your password there is a Session menu at the bottom of the screen - can you select gnome in that?

---

### Post by jczeroman on 2010-10-15
Unfortunately, there is no "session" option. There is merely an "option" link which gives four options: restart, shut down, suspend and hibernate.

---

### Post by Peter09 on 2010-10-15
Well it looks like you may have a cobbled version of Ubuntu. It may be worth downloading the latest iso and trying a fresh install - its relativley easy.
 
Its difficult to be sure what state your system is in. 
 
The only other thing you could attempt is to go into a terminal and type
 
```
sudo apt-get install ubuntu-desktop
```

---

### Post by jczeroman on 2010-10-15
If it helps, here is what the thing looks like:

---

### Post by jczeroman on 2010-10-15
> **Peter09 said:**
> Well it looks like you may have a cobbled version of Ubuntu. It may be worth downloading the latest iso and trying a fresh install - its relativley easy.
 
Its difficult to be sure what state your system is in. 
 
The only other thing you could attempt is to go into a terminal and type
 
```
sudo apt-get install ubuntu-desktop
```

Thanks for that. Let me see if I can work that out.

---

### Post by jczeroman on 2010-10-15
> **Peter09 said:**
> Well it looks like you may have a cobbled version of Ubuntu. It may be worth downloading the latest iso and trying a fresh install - its relativley easy.
 
Its difficult to be sure what state your system is in. 
 
The only other thing you could attempt is to go into a terminal and type
 
```
sudo apt-get install ubuntu-desktop
```

This did something, but the window closed before I could see the full text. It said something about being already installed.

---

### Post by jczeroman on 2010-10-15
I just installed a fresh one - works great.

---

