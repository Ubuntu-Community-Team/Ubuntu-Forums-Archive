---
title: "Login Problem"
date: 2005-07-17
forum: Desktop Environments
---

### Post by ItIsMe on 2005-07-17
My computer will not allow me to login anymore.

I installed a new GDM Theme for the login in menu but now when I start it up it has the following message;


There was an error loading the theme Ubuntu
Colors must be on the format #xxxxxx,
#1d1553300 is an invalid color


Then when I press OK It loads a different login in menu with a flower in the bottom right corner. It has the bos where you type in your username but I can't type anything in it. I can still use all the buttons in the toolbar at the bottom but it won't let me log in.

---

### Post by dave9191 on 2005-07-17
You could hit ctrl+alt+F1 (F7 to get back to gui) to drop to the command line and log in there. Once there you can change the theme back or fix the colour and restart. 

Dave

---

### Post by roland_mai on 2005-07-17
First, do what dave9191 said. 

That is Ctrl+Alt+F1 and login as yourself.

Then, killall X servers with:

```
killall -9  X gdm
``` 

Type

```
startx
``` 

to start the X window manager. The menu here is accessed through right clicking.

Open a terminal if you already do not have one up.

In the terminal type

```
gksudo gdmsetup
``` 

Here you can change the theme to one that works.

Hope this helps,

Roland

---

### Post by ItIsMe on 2005-07-20
Thanks for the help.

---

### Post by Brachabre on 2005-08-06
Swwweeeeet Thank you I just had this problem too    \\:D/

---

