---
title: "Ubuntu 10.04 Splash screen CHANGE?"
date: 2010-05-23
forum: Desktop Environments
---

### Post by Limeni on 2010-05-23
Hi, how can I change Ubuntu 10.04 splash screen? Im not using login, it logs me in automaticly, but there is that ubuntu logo with some kind of purple background that joust pokes my eyes everytime I turn on of turn off my computer.

Is there any way to change this. I installed xubuntu 15 minutes ago and there you have options to chose what splash screen to get. 

Is there any way to change splash in Ubuntu 10.04?

---

### Post by Limeni on 2010-05-23
OK here is solution. Ubuntu 10.04 uses plymouth themes for splash screen.

To change it go to Synaptic Package Manager and Quick search plymouth 
There you have some nice plymouth themes, install them. I like plymouth-theme-solar the best. 
Now when you install it, open Terminal and type this: 
```
sudo update-alternatives --config default.plymouth
```And there you chose the number of your theme to make it default theme and thats it.

Hope you find this useful. Its youst that Ubuntu default splash is... ugly, really ugly. Xubunutu has nice splash, Kubuntu too. But Ubuntus spalsh joust sucks. Hope they change it in 10.09!

Edit: I joust installed theme called: hm... cant remember whats the name of the theme, i think something like: plymouth-theme-spintynity or something like that. And when restarted my computer i got stuck on splash screen :( So i had to install Ubuntu again. SO DO NOT install that theme. Stick with the plymouth-theme-solar to be on the safe side.

---

### Post by texaswriter on 2010-05-23
Would it be possible for all the various theme elements to be customizable from ONE central location that also allows plugging into theme websites [for each individual element]  like KUBUNTU does. This would be great. I have had nothing but trouble customizing anything that wasn't the basic theme for colors, icons, mouse pointers, etc.... At least on Ubuntu. 

Kubuntu, it's so easy for me to customize everything the way I want.

---

