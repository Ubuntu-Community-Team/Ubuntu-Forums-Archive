---
title: "How to minimize a fullscreen application?"
date: 2005-12-23
forum: General Help
---

### Post by chimera on 2005-12-23
I was wondering, is there a vay to minimize a fullscreen application (like a game) in GNOME, and if there is, how do you do it?

---

### Post by jso on 2005-12-23
[QUOTE=chimera]I was wondering, is there a vay to minimize a fullscreen application (like a game) in GNOME, and if there is, how do you do it?[/QUOTE]
Maybe there's a better way, but I'd recommend hitting ALT+ESC, which switches windows.  Then you can right-click on the taskbar and actually minimize the game.  Let me know if it works (or, if someone else has a better idea, please post).

---

### Post by chimera on 2005-12-23
alt+esc doesn't seem to work in fullscreen applications

---

### Post by -varun- on 2008-07-19
bump, i know this thread is old...but i'm having the same problem

---

### Post by llama320 on 2008-07-19
Try this..

alt-space --> this opens the same dropdown menu as if you right-clicked on the title bar of a window

press "n" --> this should minimize your window

Even if the dropdown menu doesn't show up (which it should) try pressing "n" anyways, because it may be hidden behind the actual window

Good Luck

---

### Post by -varun- on 2008-07-19
alt + space, didnt work, 'space' is one of the keys recognized by the game.

i did some research on it, and it seems to be a bug in ubuntu which hasnt been fixed it :(

[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/63245](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/63245)
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/133116](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/133116)

---

### Post by llama320 on 2008-07-19
can you set a global command for minimize?
System > Prefs > Keyboard Shortcuts

I have my doubts that this will work because it wouldn't recognize alt+space but maybe you can find a key combo it'll recognize

---

### Post by -varun- on 2008-07-20
> **llama320 said:**
> can you set a global command for minimize?
System > Prefs > Keyboard Shortcuts

I have my doubts that this will work because it wouldn't recognize alt+space but maybe you can find a key combo it'll recognize

I just gave it a go, didnt work. I think the program handles all the key inputs.

You can give it a go yourself, i'm using SuperTux2 on fullscreen trying to minimize :p

---

### Post by llama320 on 2008-07-20
> **-varun- said:**
> i'm using SuperTux2 on fullscreen trying to minimize :p

Is it in the repositories? If not do you have a deb source I can put in sources.list or something?

---

### Post by soxs on 2008-07-20
sudo nano /etc/X11/xorg.conf

add "AllowDeactivateGrabs"  "1" to your "ServerFlags" Section, so ti looks like:

```
Section "ServerFlags"
# if you don't have this one, don't care
        Option          "AIGLX" "1" 
        Option          "AllowDeactivateGrabs"  "1"
# there may be some more options listed. leave them as they were
EndSection
```
save with <STRG><O>
exit with <STRG><X>

Now you should be able to windowfy a opengl window via <STRG><ALT><ENTER> though the mouse sometimes gets capotured and sometimes the whole thing stragely doesn't work (see man xorg.conf)

---

