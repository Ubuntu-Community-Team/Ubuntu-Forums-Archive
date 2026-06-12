---
title: "Cant Apply Themes"
date: 2007-08-16
forum: Desktop Effects &amp; Customization
---

### Post by damansandhu on 2007-08-16
HI , i am using kubuntu and i dont know how to apply themes , i have emerald theme manager installed , but themes dont apply when i select them , what is the problem??

---

### Post by damansandhu on 2007-08-16
somebody plz help me out

---

### Post by sergiothatguy on 2007-08-16
Sounds like you are using Beryl, am I correct? Right click the beryl icon and then select *Reload window decorator* (or something like that, I am currently using XP at the moment so I'm not sure of the exact phrasing). The selected theme should then be applied.

---

### Post by damansandhu on 2007-08-16
i have done this , but still unable to apply themes

---

### Post by joshuachad on 2007-08-16
Im not sure if emerald works for KDE but if it does type "emerald --replace" in a terminal then open your emerald manager and see if the themes stick. If that does work for you let me know and ill show you how to make it load automatically.

---

### Post by damansandhu on 2007-08-16
after that command nothing happened but the applications like firefox and others were not moving and closing. so i had to restart.

---

### Post by joshuachad on 2007-08-16
Did you install compiz-kde?

If not run these commands:
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install compiz compizconfig-settings-manager compiz-kde 

I was told you need the compiz-kde package to use window decorations in KDE.

---

### Post by joshuachad on 2007-08-16
Install this one also:

libcompizconfig-backend-kconfig


What is you graphics card? Also if you have time please copy and paste your xorg.conf file located in /etc/X11/.

---

