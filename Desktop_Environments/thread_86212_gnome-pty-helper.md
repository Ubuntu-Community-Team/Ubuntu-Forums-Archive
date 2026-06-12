---
title: "gnome-pty-helper ??"
date: 2005-11-04
forum: Desktop Environments
---

### Post by psychicdragon on 2005-11-04
What does this do exactly? It doesn't have a man page and Google provides me with practically no information.

The only GNOME app I use is Epiphany but after my computer has been on for a while I notice that there are a whole bunch of gnome-pty-helper processes running. As many as 7 at one point. :confused: 

I'm just kind of curious what it's up to...

---

### Post by Kyral on 2005-11-04
Hmm...PTYs are like terminals spawned to hold a process...I think.....

So maybe it helps to control all the processes that spawn in GNOME? I dnno really. I always just put it down as one of those "System processes that I don't wanna screw with"

---

### Post by hav0x on 2005-11-13
It has something to do with gnome-console ... i dunno but i usually kill'em (i like to screw with stuff :P) when they start to build up. This one time i had about 30 running .. i sh1t you not.
They seem to not die when you close/exit the console, must be a bug or something.

---

### Post by dmatrix on 2005-11-14
Same problem here on multiple boxes that I use gnome-terminal on. Googled some and checked bugzillas but have found nothing.

---

### Post by mcduck on 2005-11-15
if you just close the gnome terminal, it doesn't log you out, only closes the window. You have to use 'exit' to close terminals propoperly..

I had gkrellm to monitor the amount of users on my computer, and opening a terminal adds one user, but closing the terminal without 'exit' doesn't remove the users so after opening some terminals you're actually logged in to your machine as multiple users.. And you get as many pty-helpers as you have those users..

It's pretty stupid thing, I don't think that causes any serious trouble, but I'd like to just close the terminal window when I don't need it :/

---

### Post by hav0x on 2005-11-18
even using "exit" the problem remains, it's very annoying. :???:
I've witnessed it with the system-monitor open but it wont happen every time... I cant put my finger on it. Sux :(

---

