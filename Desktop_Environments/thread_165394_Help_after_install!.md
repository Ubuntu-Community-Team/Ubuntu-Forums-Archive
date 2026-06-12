---
title: "Help after install!"
date: 2006-04-24
forum: Desktop Environments
---

### Post by grumpygirl on 2006-04-24
I have done the install for ubuntu, but after it asks for login and password it stays in a DOS style format, is this normal and if so how do I proceed to the desktop?](*,)

---

### Post by ajgreeny on 2006-04-24
Did you do a server install without desktop?  If you did try:-
sudo apt-get install ubuntu-desktop
If you installed with a desktop try:-
startx
and see what happens.  Report back and someone will be able to help further, I'm sure.

---

### Post by grumpygirl on 2006-04-24
I tried startx and nothing, "just command not recoqnized".

---

### Post by nanotube on 2006-04-24
[QUOTE=grumpygirl]I tried startx and nothing, "just command not recoqnized".[/QUOTE]
so that means you installed without the desktop stuff.
run the command 
```
sudo apt-get install ubuntu-desktop
```
as suggested by the previous poster, and try again.

---

### Post by Ramses de Norre on 2006-04-24
Do this with the install cd inserted.

---

### Post by bswilson on 2006-04-24
I agree; it seems that maybe you installed the server version.  I am not sure how much/little you know about Linux, but there is a concept in Linux called **runlevels**.  I don't mean to talk down to you or insult you, so forgive me.

The term runlevel refers to a mode of operation in one of the computer operating systems that implement Unix System V-style initialization ([thanks, Wikipedia]("http://en.wikipedia.org/wiki/Runlevel")).

If you installed the server package, you'll be defautled to runlevel 3 which is "multi-user mode, plus networking".  If you log in and run startx after installing the GUI package (from the tip above), you will then be in runlevel 5, which is what you want.

If you can get to the GUI, post back and let us know; we'll help you configure your system to start at runlevel 5 all the time (if that's what you want).

---

### Post by Ramses de Norre on 2006-04-24
In fact he is in runlevel 2 and will stay in it when he installed a GUI too, the default in ubuntu is always 2. The only problem he has is that he hasn't got an X server installed. Both in console and graphical mode you'll be in multiuser + networking mode.

---

