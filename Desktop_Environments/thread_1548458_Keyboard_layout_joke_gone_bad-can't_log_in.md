---
title: "Keyboard layout joke gone bad-can't log in"
date: 2010-08-08
forum: Desktop Environments
---

### Post by MountainX on 2010-08-08
While I was away from my computer a friend changed my keyboard layout to a random layout thinking he could revert it via mouse actions only. Unfortunately, by the time I returned, my screen was locked. Now I cannot log in to the KDE session to restore the correct keyboard layout.

However, I can log in to a console. How can I change the KDE keyboard layout from a console? I'm running Kubuntu 10.04.

---

### Post by pithdillinja on 2010-08-08
Well, I don't use kde, I use gnome - but I know the keyboard properties command in GNOME is ```
gnome-keyboard-properties
``` I know there is an onscreen keyboard program for KDE (that may or may not be installed by default, I'm not sure) called ```
kvkbd
```

*note that these are both GUI programs. I don't know how to change the layout directly from console. but perhaps you can get a command line to bring up either of those programs.

---

### Post by MountainX on 2010-08-08
thanks but I cannot bring up any GUI applications. I'm in a pure console.

Still looking for kubuntu help...

---

### Post by ironic.demise on 2010-08-08
At login isn't there a "accesibility" menu that allows an on-screen to login? I know in Ubuntu 10.04 there is. It looks like a little man trying to stop a circle from collapsing in on him.

---

### Post by MountainX on 2010-08-08
> **ironic.demise said:**
> At login isn't there a "accesibility" menu that allows an on-screen to login? I know in Ubuntu 10.04 there is. It looks like a little man trying to stop a circle from collapsing in on him.

This is not login -- it's the screen lock. There is no accessibility menu or anything else that would let me change settings.

I can use Ctrl-Alt-F1 to get to a console and the keyboard layout is normal in the console. So I can login and edit any files. I just need to know what to edit.

---

### Post by ironic.demise on 2010-08-08
I'm not sure, sorry I can't help more. What's stopping you from logging off/switch user to bring up the login screen with the access menu?

---

### Post by MountainX on 2010-08-08
> **ironic.demise said:**
> I'm not sure, sorry I can't help more. What's stopping you from logging off/switch user to bring up the login screen with the access menu?

I may have one clue -- the application setxkbmap. I just need to figure out which args to pass and whether this app will do the trip when running in the console.

Regarding logoff, there is not an option to logoff from the unlock screen (unlike from the login screen). I could probably reboot from the console, but that would abnormally terminate all the running programs and it would not save open/changed files (if I had any). Plus, I am not sure that after doing that I will have any option to change keyboard layout from the login screen. If I knew for sure that I could do that, I would probably just go ahead and reboot.

---

### Post by MountainX on 2010-08-08
Solved.

Edit the file ~/.kde4/share/config/kxkbrc

Change this line to what is shown below:
LayoutList=us

Thanks to jschiwal

---

