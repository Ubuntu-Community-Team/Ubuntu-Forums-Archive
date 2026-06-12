---
title: "Screenshot via SSH."
date: 2005-12-23
forum: General Help
---

### Post by denisesballs on 2005-12-23
Does anyone know of a command line way to take a screenshot that doesn't require user interaction. For instance to take a screenshot while logged on somewhere else without having to click save like with gnome-screenshot.

---

### Post by schilcha on 2005-12-23
[QUOTE=denisesballs]For instance to take a screenshot while logged on somewhere else without having to click save like with gnome-screenshot.[/QUOTE]
What do you want to do? If you take a screenshot, you'll shoot your display (if you have one), wherever you're logged in. If you want to take a picture of some other user's display, that user has to agree -- in that case it would be easier to ask that user to send you a screenshot.

I guess I didn't quite get you right -- please give me some hints.

---

### Post by denisesballs on 2005-12-23
K, if I'm ssh'd into my home computer as the user who's home I'm in, I want to take a screenshot of the desktop. Using gnome-screenshot will shoot the save dialog onto the screen I'm logged into, which I can't see. I wanna just take a screenshot of that desktop, and save it to wherever so I can then copy to to when I am. Does that make sense?

---

### Post by artships on 2005-12-23
man xwd
-root doesn't need user intervention.
Perhaps you can launch it from cron, sort of have it on a time to go off periodically during a particular time or day.

Use xwud to view it, or gimp.

---

### Post by denisesballs on 2005-12-23
[QUOTE=artships]man xwd
-root doesn't need user intervention.
Perhaps you can launch it from cron, sort of have it on a time to go off periodically during a particular time or day.

Use xwud to view it, or gimp.[/QUOTE]

Awesome, and ftr this is how to do it:

```
xwd -out screenshot.xwd -root
```

The .xwd image is absolutely huge, but gimp handles it, then I can convert it to png or something. Thanks for the tip!

---

### Post by denisesballs on 2005-12-23
EDIT!

Actually this didn't work. Doing this for some reason takes a screenshot of the computer I am on and saves it to the client I am logged onto. Weird.

---

### Post by schilcha on 2005-12-23
Screenshots are always taken of the display your DISPLAY environment points to. So for ssh, this might be something like localhost:10.0, which points to the screen you're sitting in front of. 
Try setting the DISPLAY to ":0.0", which addresses the screen connected to the (remote) machine itself. Most likely, you'll get an access-denied-message. The user owning the display might try "xhost +" (see man xhost) to allow this...
Probably, you're easier off with VNC or something like this

(sorry for the brief answer, I'm in great hurry...)

good luck!

---

### Post by denisesballs on 2005-12-23
[QUOTE=schilcha]Screenshots are always taken of the display your DISPLAY environment points to. So for ssh, this might be something like localhost:10.0, which points to the screen you're sitting in front of. 
Try setting the DISPLAY to ":0.0", which addresses the screen connected to the (remote) machine itself. Most likely, you'll get an access-denied-message. The user owning the display might try "xhost +" (see man xhost) to allow this...
Probably, you're easier off with VNC or something like this

(sorry for the brief answer, I'm in great hurry...)

good luck![/QUOTE]

lol, thanks! That actually worked! But I only got a nice screenshot of my screensaver running, hahaha. I'm gonna have to figure out how to get around that now. Here is the command that works to take screenshots of the ssh'd computer:

```
xwd -out screenshot.xwd -root -display :0.0
```

---

### Post by denisesballs on 2005-12-23
```
killall xscreensaver
```

DUH! Thanks everyone for the help.

---

### Post by lokojones on 2008-01-12
I think you can send a signal to the mouse device, using ssh. First, look for the mouse device at /dev/input
Then send something using echo and route it to de mouse with >
Let me know if you find anything :)

---

