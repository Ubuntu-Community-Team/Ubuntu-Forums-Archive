---
title: "After removing gnome-panel from sessions nautilus does not draw desktop"
date: 2008-04-26
forum: Desktop Environments
---

### Post by err_ok on 2008-04-26
Ok just fresh-installed Hardy Heron. I got compiz and awn working perfectly... the annoying boot-up delay is gone (my reason for switching) and the problems begin.

After removing gnome-panel from sessions and then clicking save the programs i have open on reboot nautilus does not draw my desktop anymore. 

Also because of this cannot open many programs including firefox/gnome-terminal from the terminal unless i have root privileges.

When i run gnome-session-properties i get;
> could not connect to the session manager

Not really sure what's going on, any help would be brilliant i have reports to write :)

---

### Post by sanus|art on 2008-04-26
Can you run the ALT-F2? If yes than just type *gnome-panel* in it and press run. Not sure if it'll help though.

Anyway what is the reason for removing it?

---

### Post by err_ok on 2008-04-26
> **sanus|art said:**
> Can you run the ALT-F2? If yes than just type *gnome-panel* in it and press run. Not sure if it'll help though.

Anyway what is the reason for removing it?

I didn't want a gnome-panel.... ;)

I can't run anything as the user including any of the shortcut commands (alt+f2 etc...)

Running gnome-panel as root didn't really do it... Running nautilus as root got the desktop back.. but not the users and it doesn't help on restart.

---

### Post by bribri124 on 2008-04-26
Alt+F2 will probably not work for you since you do not have a panel.  I do not have any panels because I have no need for them.  It does sound like more than just gnome-panel was removed.

> 
Also because of this cannot open many programs including firefox/gnome-terminal from the terminal unless i have root privileges.


Correct me if I'm wrong, but it does sound like you can access a terminal.  If you can do this while logged in, you should be able to enter 'gnome-panel' and restore back to your desktop until we find the cause for your problem.

---

### Post by err_ok on 2008-04-26
I can get a terminal thanks to the awn terminal applet, that's what i used to open firefox.

However gnome-panel will not open and it doesn't say anything in the terminal either it just hangs...

---

### Post by sanus|art on 2008-04-26
Try to type 
```
gnome-at-visual -s
```in terminal, maybe the visual assistant gone too.

---

