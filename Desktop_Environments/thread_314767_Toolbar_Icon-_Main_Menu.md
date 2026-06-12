---
title: "Toolbar Icon- Main Menu"
date: 2006-12-08
forum: Desktop Environments
---

### Post by jpatt on 2006-12-08
I use the Ubutntu logo as my 'start' button displayed as main menu in preferences-> Menus & Toolbars. All my desktop icons are photos instead of default folder icons. I wish to change the  main menu icon with a photo as well. Possible?

---

### Post by CatKiller on 2006-12-08
I understand that although it is possible, it is tricky and poorly-documented. There are many posts from the poor souls who've tried to change the distributor-logo, and their many misadventures on the way.

---

### Post by jpatt on 2006-12-08
how about keeping the ubuntu logo but changing only a portion of the toolbar background image (instead applying to the entire bar)

---

### Post by mcduck on 2006-12-08
It's not hard at all, as long as you only want to change the menu icon that is in your panel instead of system-wide..

First, open Configuration Editor (press F2 and run gconfig-editor).
Then browse to apps/panel/objects and click through different objects until you find the one that has 'object_type' as 'menu-object'.

Now, on the line 'custom_icon' write the path to the image you want to use. then scroll down a bit and mark 'use_custom_icon'

That's it.

---

### Post by jpatt on 2006-12-09
Wow, exactly what I needed. Now I have Old Glory as my start button. TANKS!

You really should consider posting in tips and tricks. UBUNTU ROCKS!

---

### Post by iraiscoming223 on 2006-12-09
**OT:**
> You really should consider posting in tips and tricks. UBUNTU ROCKS!

This is what is called a "HAPPY USER" :mrgreen:

---

### Post by BlackHero on 2006-12-16
ty for info =)

---

### Post by crybaby on 2006-12-26
Hm I dont have any "object-type" as "menu-object". All I have is "launcher-object" and one "menu-bar".:confused: :confused: :confused:

---

### Post by munkar on 2006-12-26
> **crybaby said:**
> Hm I dont have any "object-type" as "menu-object". All I have is "launcher-object" and one "menu-bar".:confused: :confused: :confused:

me neither....

---

### Post by mcduck on 2006-12-27
This doesn't work for menu bar applet (the one with Applications, Places and System menus). This is for main menu-applet, that only has one button that combines all those menus, kind of like  Start-button from windows.

To change the logo for menu bar applet I think you need to change the imge file from the icon theme you are using.

---

### Post by crybaby on 2006-12-28
Ah, ok thanks. Now it works

---

### Post by ovidescu on 2007-01-15
> **mcduck said:**
> It's not hard at all, as long as you only want to change the menu icon that is in your panel instead of system-wide..

First, open Configuration Editor (press F2 and run gconfig-editor).
Then browse to apps/panel/objects and click through different objects until you find the one that has 'object_type' as 'menu-object'.

Now, on the line 'custom_icon' write the path to the image you want to use. then scroll down a bit and mark 'use_custom_icon'

That's it.

Another happy user. Thank you. Ubuntu rules, Windows drools !

---

### Post by gamgee911 on 2007-05-24
all i can do when i try to change it is just hit the false/true button. it won't let me change the file

---

