---
title: "Compiz hotkey problem - destop left/right"
date: 2007-07-22
forum: Desktop Effects &amp; Customization
---

### Post by cccccccc on 2007-07-22
Hello,

 I have Ubuntu 7, witch desktop effects (compiz) + compiz-tray-icon (after start up). Everything is OK, except, that I am not able to setup hotkey for rotating desktop left/right. Since (I dont know why) in gnome-compiz-preferences there is no such option (System-> Preferencies -> Keyb. Shortcuts won't work either) I tryed gconf-editor (all the time with sudo), and there apps -> compiz -> plugins -> plane -> allscreens -> options: plane_left/right_key. But no matter what I set there, I can turn to left/right desktop only by default Control + Alt +Left/Right (I tryed logout/restart)! Can I change somehow this setting? Thx!

  Cyril

---

### Post by ddrichardson on 2007-07-22
compiz-settings-manager will let you configure these easily

---

### Post by cccccccc on 2007-07-22
even if i do not use stuf which is not in repository i tryed this one. its brilliant, but i am not able to run cube and multiple desktops here:(

---

### Post by ddrichardson on 2007-07-22
Do you have everything up and running, including setting horizontal virtual size to 4?

---

### Post by cccccccc on 2007-07-22
:) sorry, i found out, i have to set up desktop in General. I can not change this plugin first (all the time i checked it, it automatically unchecked). But now I some how manage. Hotkeys work too! Thanks!

---

### Post by sevenearths on 2008-05-03
Has anyone got any ideas why this might happen. Some of my hot keys work (like slow animations in 'general' Shift+F10) but the ones that don't work are in blue for some reason. I'm wondering if it something to do with the way the keyboard might be mapped!

---

### Post by sevenearths on 2008-05-03
Changed my keyboard to 105 and that sorted it out for me :)

---

