---
title: "Unicode in Gnome"
date: 2005-06-06
forum: Desktop Environments
---

### Post by sancho21 on 2005-06-06
Hi all! 

Does anyone know how to set unicode in gnome so I can read japanese, koreans in gnome-terminal, shell, nautilus, etc?  :neutral: 

Thanks

---

### Post by sancho21 on 2005-06-06
Sorry, I was not supposed to ask here, was I?

---

### Post by crvendramini on 2005-06-06
Maybe, the thread next can help you: [here](http://ubuntuforums.org/showthread.php?t=30803)

---

### Post by Alexander Kirillov on 2005-06-06
[QUOTE=sancho21]Hi all! 

Does anyone know how to set unicode in gnome so I can read japanese, koreans in gnome-terminal, shell, nautilus, etc?  :neutral: 

Thanks[/QUOTE]
 Ubuntu Hoary uses unicode (to be precise, utf8) by default. Type "locale" and if you see soemthing like en_US.UTF-8, it means you are using utf8. You should be able to use Japanese or Korean in terminal,  Nautilus, all graphical app right away (if you have fonts). Of course,  to type in Korean, you will also need to switch your keyboard layout (using Preferences-Keyboard). 

There may be problems, e.g., if you want to share files between different computers, or communicate with people who use different encoding. But  using unicode on a single computer should work out of the box.

---

