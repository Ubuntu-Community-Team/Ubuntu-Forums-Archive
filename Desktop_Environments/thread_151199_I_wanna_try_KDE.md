---
title: "I wanna try KDE"
date: 2006-03-27
forum: Desktop Environments
---

### Post by Granpooba on 2006-03-27
I've very recently installed Ubuntu.  My first experience with Linux!!  I'm apparently using Gnome.  It's okay, I guess, but I'd like to try something else.  Could someone tell me in simple terms just how to go about changing desktops??   I know how to bring up a terminal, if that helps..!!  You'd need to start there..  :)   Thanks !!

---

### Post by towsonu2003 on 2006-03-27
It's very easy in Ubuntu. open up a terminal and ```

sudo apt-get update
sudo apt-get install kubuntu-desktop
```

this will download and install kde. wait until it finishes, log out of gnome, and choose "kde" on the login screen's "session" option. 

this may change the splash screen (the first thing you see during boot, with a process bar on it) from ubuntu (brown) to kubuntu (blue?). I'm sure there is a way to undo it, but I don't know of it. Don't worry about it. Mine changed to Xubuntu (uses xfce4 instead of gnome or kde) but it's kinda cool :PpP

---

### Post by aysiu on 2006-03-27
I would recommend doing this instead: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` Makes it easier to remove KDE later if you don't like it.

---

### Post by lupine_nickt on 2006-03-27
?

I fail to see a difference between using aptitude and apt-get for command-line options.

You could do it with synaptic as well, if you wanted... all three use the same config files, surely?

xF,

...Nick

---

### Post by Granpooba on 2006-03-27
Okay..  thanks guys...  I'm now running KDE..  I see a few differences, so far..  Now, I thought I might not have the brown desktop anymore but, of course, I do.....  so..  I need to figure out how to use a picture of my choice as the desktop background (or even some color besides brown I would like better.  I assume this is possible...  What I'm really worried about is that my password to get into root isn't working... I don't really need to get in as root, yet, but..,  I know I'm gonna..  Again..  Thanks, y'all..

Granpooba

---

### Post by aysiu on 2006-03-27
[QUOTE=lupine_nickt]?

I fail to see a difference between using aptitude and apt-get for command-line options.[/QUOTE] I explained in the post above what the difference is. You can also see post #19 of [this thread](http://www.ubuntuforums.org/showthread.php?t=96048) for more details.

---

### Post by towsonu2003 on 2006-03-27
[QUOTE=Granpooba]What I'm really worried about is that my password to get into root isn't working... [/QUOTE]
so when you type ```
sudo ifconfig
``` and type in your own password, what does it say?

---

### Post by lupine_nickt on 2006-03-27
Ah - gotcha now. Thanks :). 

xF,

...Nick

---

