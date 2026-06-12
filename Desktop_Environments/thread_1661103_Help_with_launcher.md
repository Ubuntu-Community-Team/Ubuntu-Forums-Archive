---
title: "Help with launcher"
date: 2011-01-06
forum: Desktop Environments
---

### Post by kyral210 on 2011-01-06
I need to set up a desktop launcher to run a script in terminal automatically (as opposed to double click on script - run in terminal).
 
Someone mentioned right clicking the desktop and selecting Create Launcher. All well and good, but how do I them make it run my script in the terminal automatically?

---

### Post by An Sanct on 2011-03-21
Right click on the desktop, select "Create Launcher", in the dropdown, select "Application in terminal" then select the script in the "Command:" input

the name and descriptions are up to you.

---

### Post by Krytarik on 2011-03-21
> **An Sanct said:**
> Right click on the desktop, select "Create Launcher", in the dropdown, select "Application in terminal" then select the script in the "Command:" input

the name and descriptions are up to you.
Unfortunately, there seems to be a bug currently regarding those option.

So you may have to leave "Application" chosen and set the "Command" like this:
```
gnome-terminal -x sh -c "terminal_command"
```Greetings.

---

### Post by An Sanct on 2011-03-21
> **Krytarik said:**
> Unfortunately, there seems to be a bug currently regarding those option.

So you may have to leave "Application" chosen and set the "Command" like this:
```
gnome-terminal -x sh -c "terminal_command"
```Greetings.

Bug? Can you elaborate a little bit more on this?

---

### Post by Krytarik on 2011-03-21
> **An Sanct said:**
> Bug? Can you elaborate a little bit more on this?
Ah, forget about that! Upon trying to reproduce the previously experienced behaviour, I noticed that it was before I learned that you can't run some commands through a launcher like you do at the shell. When enclosing them like this
```
sh -c "command1; command2"
```
they run as well. At least I guess it was that, but I'm not sure. Anyway, at least as of now it seems to be all well.

---

### Post by kyral210 on 2011-07-23
As it turns out double clicking the .sh file and cicking run isn't much easier than a desktop launcher, so problem solved.

---

