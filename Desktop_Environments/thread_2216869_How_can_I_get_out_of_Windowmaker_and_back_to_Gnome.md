---
title: "How can I get out of Windowmaker and back to Gnome without an Application Menu?"
date: 2014-04-14
forum: Desktop Environments
---

### Post by bigell63 on 2014-04-14
I'm really stuck and would greatly appreciate some help to get home to my safe place!

I logged in to Windowmaker last night to have a look at it and, once suitably appalled, tried to return to the comfort of my Gnome desktop only to find that I cannot.

There is nothing whatsoever in the Wmaker application menu and I can't figure out how to put Sessions in it from the config icon thingy. When I reboot the computer takes me straight to wmaker with no option to login in to another environment.

I don't know what command will log me out of wmaker - tried logout, halt, shutdown etc...

I can find plenty of advice on how to INSTALL wmaker or use virtual desktops (ctrl-alt-f7 etc)

But nothing on how to get out of it.

---

### Post by QDR06VV9 on 2014-04-14
Have you tried while being logged in WM 
Key SeQ "control+alt+F1"
You then you can try.
```
   exec ***gnome-session*** & 


```
or even.
```
gnome-session
```

---

### Post by bigell63 on 2014-04-15
Thank you runrickus.

I tried that and got a fatal server error - another window manager is already running

I tried unity --reset and got the same error which necessitated me deleting a file called X)-lock from /tmp. I'm going to restart and try  at login time and see if I can get the login screen back.

I can get my gnome desktop back with the command you gave me, but the dash etc are missing.

---

### Post by bigell63 on 2014-04-15
Okay I did it.

I ran :

```
 killall wmaker && gnome 
```

and got dropped back to the login screen and GNome and Unity have loaded properly.

---

### Post by su:bhatta on 2014-04-15
Please mark the thread as Solved using the Thread Tools at the top right of the page !

---

### Post by bigell63 on 2014-04-16
Thank you su:bhatta. I didn't know how to do that. :)

---

### Post by su:bhatta on 2014-04-16
No problem bigell63.

In case you are interested, all you had to do was to do a right mouse-click in the desktop. 
That would have opened up the menu, and you would have to choose 'Exit' (last option in the menu) to get out of the Window maker session.

---

