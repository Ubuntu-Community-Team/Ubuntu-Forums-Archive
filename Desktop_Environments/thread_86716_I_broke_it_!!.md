---
title: "I broke it !!"
date: 2005-11-06
forum: Desktop Environments
---

### Post by 3guk on 2005-11-06
So last night I thought I don't use evolution anymore so I went into synaptic to remove it and all of its extras. Basically anything that had evolution in front of it. 

Clicked apply and it said it would modifty nautilus and I just let it do its work.

Everything seemed fine until I restarted and, now linux starts with just a brown screen, no taskbar no anything just a mouse and a brown screen.

If it helps I use a dual boot system.

Can anyone tell me how to sort this as Ubuntu is my fav OS and Id like to be able to carry on using it.

---

### Post by nSTKo on 2005-11-06
Maybe you can reinstall it (Ubuntu)? It always works for me. :p

Edit: Yesterday i was "experiment'ing" with Ubuntu, and i had the same problem, i installed fluxbox and used it for 1 day, today i reinstall'ed Ubuntu and all works fine.

---

### Post by RAOF on 2005-11-06
If you removed everything evolution related, you'll also have removed some things which are required for Gnome (the desktop environment) to work.  To re-install to a workable system, the easiest thing will be to press Ctrl-Alt-F1 once Ubuntu has booted.  This should get you to a terminal login, with a
"username:" prompt.  

Login, and then run
```

sudo apt-get install ubuntu-desktop

```
This will install all of the base ubuntu packages again.  Then reboot using 
```
sudo shutdown -r now
```

It should now boot back into Gnome, and all the graphical goodness.

---

### Post by Sirin on 2005-11-06
[QUOTE=3guk]So last night I thought I don't use evolution anymore so I went into synaptic to remove it and all of its extras. Basically anything that had evolution in front of it. 

Clicked apply and it said it would modifty nautilus and I just let it do its work.

Everything seemed fine until I restarted and, now linux starts with just a brown screen, no taskbar no anything just a mouse and a brown screen.

If it helps I use a dual boot system.

Can anyone tell me how to sort this as Ubuntu is my fav OS and Id like to be able to carry on using it.[/QUOTE]

Install KDE and fix it from there using Synaptic or Kynaptic. I know, you may absolutely hate KDE as much as Windows, but doing it the command line way is very irratating. After you reinstall Gnome, you may ditch KDE or do whatever the hell you want with it. ;)

---

### Post by linbetwin on 2005-11-06
ALT + F2, then type synaptic to open it and reinstall evolution. Hope this helps.

---

### Post by 23meg on 2005-11-06
Check if you have uninstalled the ubuntu-desktop package and see if reinstalling helps if it's gone.

---

