---
title: "how do i make a startup application start on tray?"
date: 2009-04-04
forum: General Help
---

### Post by chriskin on 2009-04-04
i want the "liferea" application to start when my computer starts, but i would like it to start as a tray icon, not as a window
can you help me?

:popcorn:

---

### Post by ukblacknight on 2009-04-04
If the program itself doesn't natively put itself into the notification area, you can use a program called AllTray

```
sudo apt-get install alltray
```

When that is installed, you can add your program to the start up items normally, but issue the command "alltray" before the command for the program, for example

```
alltray evolution
```

would start evolution in the notification area.  You can add programs to start up in System > Preferences > Sessions.

---

### Post by chriskin on 2009-04-04
liferea goes to tray when you close it, so it can be there natively

since alltray leaves the window to be seen by the window list screenlet, i would like to get the command you write after the app's name in the terminal to make it go to tray at startup
:S

---

### Post by ukblacknight on 2009-04-04
Ah I see!  I don't really know then, you could try:

```
man liferea
```

to see if there is an option to start the program minimised in the tray...

---

### Post by chriskin on 2009-04-04
> **ukblacknight said:**
> Ah I see!  I don't really know then, you could try:

```
man liferea
```to see if there is an option to start the program minimised in the tray...


yes! i found it there

thank you very much :)

---

### Post by ukblacknight on 2009-04-04
No problem :)

---

