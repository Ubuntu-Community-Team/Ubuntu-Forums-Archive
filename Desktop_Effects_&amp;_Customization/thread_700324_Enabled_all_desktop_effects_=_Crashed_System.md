---
title: "Enabled all desktop effects = Crashed System"
date: 2008-02-18
forum: Desktop Effects &amp; Customization
---

### Post by leoblack9 on 2008-02-18
I just found a way to enable compiz on my gutsy. By using xgl I was finally enable the desktop effects. I was too excited, and quickl downloaded ccsm / compiz custom settings manager or something.

I've mistakenly checked all of the boxes, even though it looks cool, it instantly freezes whenever any kind of window pops up. I seem to have forgotten that I only have an integrated graphics card running. 

Please help me here, I don't know how to fix this since opening any type of window would instantaneosly freeze my whole system, therefore my only solution is the power switch.

---

### Post by justleen on 2008-02-18
just a hunce.  on the login screen you can select what kind of session you want.. choose "failsafe gnome", and see if you can change the appearence setting back to normal there..


(another very rigorous way might be to delete the .gconf folder from a terminal..)

---

### Post by ajgreeny on 2008-02-18
Startup the computer, Ctrl+Alt+F1 to get a console, login, then enter ```
metacity --replace
``` and go back to the gui with Ctrl+Alt+F7.  Now you should be able to get to the CCSM window and get rid of some of the compiz plugins you've activated, and go back to a lesser set of compiz by using System>Preferences>Appearance in the menu.

---

### Post by leoblack9 on 2008-02-18
Is the console a kind of window? Because I tried hitting alt+F2 and it froze.

I seem to have enabled automatic login, so I can't open failsafe gnome T_T

---

### Post by ajgreeny on 2008-02-18
If you hit Ctrl+Alt+F1 you will get a screen that looks a bit like a dos window but will say **hostname login: **with hostname being whatever you called it at install.  At that point, login with your username and then password (nothing shows on screen when you type your password but don't worry, just hit enter and you will get logged in OK).  Now type ```
metacity --replace
```NB in a senior moment in my last post I typed that the wrong way round, whoops!  Then continue as I said last time.

---

### Post by leoblack9 on 2008-02-18
I successfully entered the console mode, and I was able to log in. But the problem there is that when I type metacity --replace, it doesn't work. Says something about dwm manager cannot open x, sorry I can't quite recall what was written there, I only remember that it didn't work so I'm still stuck with an ice-cold, freezing os.

---

### Post by chavanak on 2008-02-18
You have to mention what messsage was given back when you typed metacity --replace.

Try the other option on the login window press F10/F11 and in sessions select failsafe gnome and try if that works

---

### Post by ajgreeny on 2008-02-19
I seem to remember that even with auto login enabled, if you log out for a new session you will then get the login screen appear, where you can chose the failsafe-gnome.  Give it a try and you may be OK.

---

### Post by leoblack9 on 2008-02-19
It worked, now its back to normal. Thank you for all of your help. But would the errors somehow scar my system like windows? I'm worried because I've used the off button without shutting it down because it froze on me, several times.

---

### Post by chavanak on 2008-02-19
Hmm as far as i know ext3 manages stuff much better than ntfs!!! Enjoy your linux box. Be happy no worries!!! every 30 mounts the disk will be checked and errors, if any will be rectified.
 You can also run a manual disk check.

---

