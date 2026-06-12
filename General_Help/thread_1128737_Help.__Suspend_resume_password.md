---
title: "Help.  Suspend resume password"
date: 2009-04-17
forum: General Help
---

### Post by Amerinidiot1231 on 2009-04-17
On a laptop when the lid is closed the laptop suspends.  Upon opening the lid you are prompted for a password.  How can you prevent this so you can go straight to the desktop?

My grandparents are in town and my grandfather likes to play a game, but my laptop needs to suspend when he is done and I don't want him to need to type in a password.

The laptop is running ubuntu 8.04

---

### Post by James_Lochhead on 2009-04-17
I think it is power management in System > Administration (might be preferences). It is there somewhere anyway, I use KDE now so I cannot check.

---

### Post by Amerinidiot1231 on 2009-04-17
Power Management does not have any options relating to it, nor does screensaver.

---

### Post by cellulararrest on 2009-05-19
I seem to be having this problem in Jaunty as well. I have unchecked lock after suspend everywhere I can find it (Gconf-editor, power management, screensaver). For some reason it always wants to lock the user. Plus it kills all the programs.

---

### Post by dixonstalbert on 2009-05-21
to the original poster:

open a terminal and type gconf-editor

navigate to /apps/gnome-power-manager/lock and uncheck suspend and whatever else you dont want to have restart with the lock screen

close gconf-editor


to last poster: 

Originally I ran "sudo gconf-editor" as I thought only admin could change gconf settings. i unchecked all the locks but I still got the screen *when I logged in as my normal account* I found out I had to run gconf-editor without the sudo to get it to change settings for my gnome session. Now it works!

---

### Post by miniyak on 2009-06-24
thanks, this works great. Also gives light to other settings that are missing from the main ui

---

### Post by danielbu on 2009-11-24
Awesome! I didn't have this problem in previous versions, but since updating to Karmic I have not been able to get around it until now.:D

---

