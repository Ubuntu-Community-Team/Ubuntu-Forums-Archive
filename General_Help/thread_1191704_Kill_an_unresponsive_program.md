---
title: "Kill an unresponsive program"
date: 2009-06-19
forum: General Help
---

### Post by enchance on 2009-06-19
How do I kill an unresponsive program from the terminal? Like the ctrl+alt version for ubuntu.

---

### Post by ManiacDan on 2009-06-19
From the terminal?  CTRL+C will exit the current program.  If that doesn't work, CTRL+Z will make it a background process, and you can ps auxwww | grep <programName> and kill it with the "kill" command.

-Dan

---

### Post by Gunman1982 on 2009-06-19
My preferred method is: 'killall program_name' and if that doesn't help 'killall -9 program_name'. i.e. : 'killall firefox-bin' and whoosh firefox is gone ;-)

You can kill programs through their process id (pid) too: 'kill [some digits]' ie: 'kill 9152' which kills the program with the pid 9152.

---

### Post by philinux on 2009-06-19
If you ever want a gui then use system>admin>system monitor. Processes tab. Right click on the app. 

Also right click top or bottom panel and choose add to panel. Scroll down to Force Quit applet.

---

### Post by enchance on 2009-06-19
> **Gunman1982 said:**
> My preferred method is: 'killall program_name' and if that doesn't help 'killall -9 program_name'. i.e. : 'killall firefox-bin' and whoosh firefox is gone ;-)

You can kill programs through their process id (pid) too: 'kill [some digits]' ie: 'kill 9152' which kills the program with the pid 9152.

How do I find out the pid and program name of the program I want to kill?

---

### Post by wojox on 2009-06-19
type in terminal

top

it will show PID's and apps

I don't understand why you would want to kill an unresponsive program if you don't know the name of it ? How do you know it's unresponsive when you don't know what your looking for ?

---

### Post by enchance on 2009-06-19
What's the difference between kill and killall?

---

### Post by Agent ME on 2009-06-19
kill takes a pid as the argument, killall takes the program name (and it will try to kill everything with that name).

Another way to look at the processes running is with the ps command. "ps -fe" will list all processes running, and "ps -fu *user*" will list all processes owned by *user*.

---

### Post by t0p on 2009-06-19
> **Agent ME said:**
> kill takes a pid as the argument, killall takes the program name (and it will try to kill everything with that name).


**pkill** also takes the program name.

---

### Post by ManiacDan on 2009-06-22
I actually use:
```
ps auxwww | grep <programName> | awk '{print $2}' | sudo xargs kill -9
```-Dan

---

