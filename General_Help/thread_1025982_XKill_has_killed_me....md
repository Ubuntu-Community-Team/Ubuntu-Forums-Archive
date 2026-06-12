---
title: "XKill has killed me..."
date: 2008-12-30
forum: General Help
---

### Post by rodjar on 2008-12-30
Hi all, a game froze and I read online that ctrl+alt+esc is the best way to force quit something. I made the mistake of clicking on the application in the dock and it force quit the dock, not the game! I panicked and clicked on the top menu bar while still in xkill mode. I desperately need to restart the system tray and other essential components. What's the best way of doing this?

---

### Post by hansdown on 2008-12-30
Hi rodjar.

Right click an empty space on the toolbar, click "add to panel, and a list will come up.Choose the ones you want and add to panel.

---

### Post by rodjar on 2008-12-30
the problem is I don't have a toolbar! The toolbar has been killed with xkill. Is there a way to start all the default processes in xubuntu?

---

### Post by hal8000 on 2008-12-30
Press ctrl-alt-F1

this will take you into console mode.
log in with your normal user ID and password then type

sudo shutdown -r 0


this will reboot ubuntu and your panel and icons should reappear.

---

### Post by rodjar on 2008-12-30
this doesn't seem to work as the system logs into the previous session automatically. is there something I can enter into terminal that would launch the bar again? alternatively, is there a way to restart and force a new session?

---

### Post by rodjar on 2008-12-30
anybody?

---

### Post by hansdown on 2008-12-30
Hi rodjar.

I found a useful link.  [http://ubuntuforums.org/archive/index.php/t-258171.html](http://ubuntuforums.org/archive/index.php/t-258171.html)

Ctrl> alt> backspace was what you needed before.
You can still use ctrl> alt> f1 to get the terminal for these commands.

---

### Post by cb34 on 2008-12-30
i dont quite understand what's goin on there, but could it be as simple as restarting your gnome or kde session but the problem is you dont know the commands, hmmm? dont know if this will help you, but to restart gnome for instance.. from ctrl-alt-F1 or 2 or 3.....6 do:
```

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

```
that's gdm for gnome, i don't know off hand what the commands are for kde etc. but quick search may help if that's what you need.

edit-> ya, what ^^handsdown^^ said. [noparse]#:-P[/noparse]

---

### Post by MaxIBoy on 2008-12-30
For future reference, if you get a lockup, use ctrl-alt-backspace. 

If you don't have the toolbar anymore, and you're using GNOME, you should be able to alt-f2 and run gnome-panel.

EDIT: sorry, didn't see the "xubuntu" tag. For Xfce, you want to run xfce4-panel.

---

### Post by shad0w_walker on 2008-12-30
Try this:

Press Alt+F2 to open a run window, then run this:

```
gnome-panel
```

---

### Post by Slim Odds on 2008-12-30
> **cb34 said:**
> 
```

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

```
```
sudo /etc/init.d/gdm restart
```would be a little easier......

---

### Post by cb34 on 2008-12-30
i thought of that, and it should work, but sometimes it doesn't work as well as stopping first, then starting.

same thing.. i guess.

---

### Post by SlipperyPete on 2009-01-10
rodjar I had the same problem.  I'm running Xubuntu 8.10 and accidentally "xkill"ed the panels.  Rebooting was not helping since Xubuntu remembers your settings and opens them the same way.

First thing I tried (after reading a few forums) was

```
xfce4-panel &
```

to relaunch the panel.  That worked, but as soon as I close the terminal window the panels were gone again.  What I had to do was use the above code, then reboot Xubuntu.  When it opened again the panels stayed once the terminal window was closed.

Maybe there is a better way to do this (i.e. a modifier on the code) that someone with more experience with the linux terminal can suggest?

---

### Post by Slim Odds on 2009-01-10
> **SlipperyPete said:**
> ```
xfce4-panel &
```to relaunch the panel.  That worked, but as soon as I close the terminal window the panels were gone again.  What I had to do was use the above code, then reboot Xubuntu.  When it opened again the panels stayed once the terminal window was closed.

Maybe there is a better way to do this (i.e. a modifier on the code) that someone with more experience with the linux terminal can suggest?

Try this:```
nohup xfce4-panel &
```

---

