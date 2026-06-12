---
title: "Lost all Desktop Icons!"
date: 2008-08-05
forum: Desktop Environments
---

### Post by bunny_basher on 2008-08-05
Hello, I have lost all my desktop icons! I ave tried reinstalling nautilus and stuff but I can't find out how to get them all back. Any help would be appreciated!

---

### Post by kirsis on 2008-08-05
I just now encountered a bug where Nautilus didn't show any icons on my desktop. What I did was simply "killall nautilus" and when it restarted, it worked fine. 

However, if even a reinstall+restart hasn't helped then maybe you've somehow deleted the files by accident? Check if there's anything in your ~/Desktop folder. 

Otherwise file a bug report.

---

### Post by bunny_basher on 2008-08-05
it has just got worse! Now I havent even got AWM to open a terminal or anything (I am posting via PS3 lol!) Is there any way of getting a terminal open without clicking anything? lol

---

### Post by gjoellee on 2008-08-05
no...not as I know...have you tried to boot in failsafe mode or something...you should try that

---

### Post by sayakb on 2008-08-05
Alt+F1 opens up the menu.
Anyway, at a terminal, try executing **nautilus**
Plus, press Alt+F2, type in **gconf-editor**, and navigate to /apps/nautilus/desktop and check the relevant checkboxes.

---

### Post by kirsis on 2008-08-05
> **bunny_basher said:**
> it has just got worse! Now I havent even got AWM to open a terminal or anything (I am posting via PS3 lol!) Is there any way of getting a terminal open without clicking anything? lol

Alt+F2 -> Enter "gnome-terminal" -> Press Return

Or switch to a different tty (Ctrl+Alt+F1-6; get back with Ctrl+Alt+F7)

Or press Alt+F1 and navigate with arrow buttons, choose the app and press Return

---

### Post by bunny_basher on 2008-08-05
> **LinuxIsInnovation said:**
> Alt+F1 opens up the menu.
Anyway, at a terminal, try executing **nautilus**
Plus, press Alt+F2, type in **gconf-editor**, and navigate to /apps/nautilus/desktop and check the relevant checkboxes.

i would, but Alt+F2  doesnt seem to bring anything up!

---

### Post by kirsis on 2008-08-05
I think the gnome-panel is responsible for the Alt+F2 box. If that hasn't started, maybe the whole session wasnt launched for some reason.

Try switching to a different tty and executing

```
DISPLAY=:0 gnome-session
```

---

### Post by bunny_basher on 2008-08-05
> **kirsis said:**
> I think the gnome-panel is responsible for the Alt+F2 box. If that hasn't started, maybe the whole session wasnt launched for some reason.

Try switching to a different tty and executing

```
DISPLAY=:0 gnome-session
```

all that gave me was a load of errors and a "failed to open file" lol. Do i need to change the permissions for accessing the home directory or something? Cheers for the help so far btw!

---

### Post by kirsis on 2008-08-05
Does it mention which file it can't open?

Does this file exist?
```

/usr/share/gnome/default.session

```

And this?
```

~/.gnome/session

```

What if you run:
```

DISPLAY=:0 gnome-session --failsafe

```



It could be related to the session not starting up properly but I don't really have a clue as to why or how, just guessing here :) How did this happen in the first place? Did you install/modify anything?

---

