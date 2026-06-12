---
title: "How do you do a hard program quit?"
date: 2006-06-30
forum: Desktop Environments
---

### Post by chadcan on 2006-06-30
Hi,

Newbie here, I looked around and could not find an answer to this question. Sorry if this is repleat. 

I am running Gnome in 6.06. Sometimes when I have 5 or more programs running , one of my programs would freeze. Most of the time I know which one it is. How to I do hard application quite? Like in windows you can do a ctl+alt-delete and end the task. Sometimes it would completely slow down the machine and not allow you to launch any more programs like the terminal to execute anything. 

Another question is sometimes a program would take up the foreground of the OS, covers the whole screen and not have a quit button (or I just don't know where it is). How do you get out of these as well? 

Chad

---

### Post by raptros-v76 on 2006-06-30
well, if something really messes up and your sorta desperate, hit ctrl+alt+f1 to enter a terminal thing, log in, and do pkill <program name>

---

### Post by Blazeix on 2006-06-30
Also, if everything is completly locked up, and you can't even switch to the terminal thing for the above solution, hit control-alt-backspace. This will quit everything and either put you at the login screen or a text environment. If it brings you to the login screen, simply relogin; if it brings you to the text environment, you can type 'startx' to restart the graphical user interface.

---

### Post by chadcan on 2006-06-30
Thank You, This is awesome. I am loving this distrubution mainly due to forums like this help forum. I got an answer in less the 30 minutes.

If anyone has any other suggestions please post I will keep checking just in case anyone post more ideas.

Chad

---

### Post by shrift on 2006-06-30
You can use the system monitor app. It is in System>Administration>System Monitor.

Or if for some reason you don't like the menus, you can launch it from a terminal, or press "alt+f2" to open a run command box. Then type in "gnome-system-monitor".

Or, from a terminal, you can use "top". Top is a good command, it's a bit less user friendly than the system monitor, but you can run it from a terminal.

---

