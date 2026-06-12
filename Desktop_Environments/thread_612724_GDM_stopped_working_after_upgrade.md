---
title: "GDM stopped working after upgrade"
date: 2007-11-14
forum: Desktop Environments
---

### Post by king minger on 2007-11-14
Hi guys

After an upgrade from feisty to gutsy went slightly wrong (network update, and lost net connectivity 3/4 through) I have managed to salvage the install to a point where as it boots, the progress bar fills all the way up, then goes to blinky cursor top left of the screen, then finally to black screen (off) and no response to anything except power button for 5 seconds.

I think the problem is with GDM (not everything has fully updated and i think GDM was one of the things mentioned in the list of failed installs) since if I disable the display manager (by commenting out the line "/etc/X11/gdm" in the /etc/X11/default_display_manager file) I can get to a text login.

my problem now is where do I start to diagnose what's borked and how to fix it?
what logs will give me the info to start to get this fully operational?

Can I swap to KDM by changing /etc/X11/gdm to /etc/X11/kdm in default_display_manager? or is there something else?

btw, haven't tried doing a plain old startx after logging in yet... I'm at work and the lappy's at home.

it's a dell latitude D600 1.4 Pentium-M
I had the system running nicely under feisty since it was out under RC release

Cheers!

---

### Post by bigken on 2007-11-14
at the prompt try this 

sudo apt-get update

sudo apt-get upgrade

startx

you might also have to run

sudo dpkg-reconfigure xserver-xorg config

---

### Post by king minger on 2007-11-14
cool.
I'll try that when i get home

---

### Post by bigken on 2007-11-14
another thing try at the prompt 

sudo apt-get dist-upgrade

---

### Post by king minger on 2007-11-14
it was doing a dist-upgrade that got me in this mess in the first place ;)
will be doing this about 8PM (uk - ah you're in Slough:) currently in woking)

---

### Post by bigken on 2007-11-14
if you run it again it might just repair its self

---

### Post by ajopaul on 2007-11-14
If nothing works u can install xdm

and

```
 sudo dpkg-reconfigure gdm 
```

---

### Post by king minger on 2007-11-14
All sorted! :)
a combination of the above got everything up and running.
there are a few loose ends to tie up, but the show stoppers are fixed. can't say exactly what it was, but the steps in post 2 tidied everything up.

Cheers guys!

---

