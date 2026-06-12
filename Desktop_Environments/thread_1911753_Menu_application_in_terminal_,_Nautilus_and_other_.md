---
title: "Menu application in terminal , Nautilus and other apps"
date: 2012-01-19
forum: Desktop Environments
---

### Post by rafanto on 2012-01-19
I have a problem to display the menu commands in the window of the nautilus and the terminal (in simple words can not display the file .. help etc..) I see the bar but no writing .. 

[IMG]http://imageshack.us/photo/my-images/18/problemamenu.png[/IMG]


[http://imageshack.us/photo/my-images/18/problemamenu.png/](http://imageshack.us/photo/my-images/18/problemamenu.png/)

I use Ubuntu 11.10 x64 with Gnome Shell

---

### Post by raja.genupula on 2012-01-19
i think something went wrong .
**sudo apt-get install --reinstall gnome-shell**
try that once in terminal . All the best.

---

### Post by rafanto on 2012-01-19
> **raja.genupula said:**
> i think something went wrong .
**sudo apt-get install --reinstall gnome-shell**
try that once in terminal . All the best.

This solution don't change the problem.
:(

---

### Post by raja.genupula on 2012-01-19
Hi install dconf-tools
open your terminal and type this 
sudo apt-get install dconf-tools

then open your terminal and type  dconf-editor

and then click at org -> globalmenu and uncheck enabled.

logout or restart needed to apply the changes.

let me know what you got . All the best.

---

### Post by rafanto on 2012-01-20
I solved the problem completely uninstalling gnome-shell 

login to Unity and with terminal launch 

[FONT="Courier New"]sudo apt-get remove gnome-shell [/FONT]

after this step, proceed with 

[FONT="Courier New"]sudo apt-get install gnome-shell[/FONT]

---

### Post by raja.genupula on 2012-01-20
but in future if you got the problem again please use the above one .  I am sure it will work fine for you . 

please mark the thread as solved from thread tools.
Thank you

---

