---
title: "Fluxbox - some apps load, some apps don't"
date: 2006-03-31
forum: Desktop Environments
---

### Post by technasma on 2006-03-31
Maybe April fools day was the wrong time to start using linux!! I'm a complete newbie so please slap me about if the need arises.

I installed Ubuntu with the server configuration... I want something very streamlined. I have installed X, Fluxbox (dopey's latest .deb), Synaptic, dillo, xterm, and abiword. From the shell X successfully loads (from startx) and fluxbox starts. The menu works and I can load dillo and abiword but I can't load Synaptic (clicking on the menu item does nothing) and xterm hasn't even shown up in the menu... 

I haven't loaded a session manager (xdm/wdm/gdm) because I don't want a graphical login... could this be the problem... am I missing some component?

---

### Post by stuporglue on 2006-03-31
It might be permissions

Synaptic needs super user permissions to start, I don't think fluxbox's menu generator knows that. Edit fluxbox's menu (in your favorite text editor) -- It should be at ~/.fluxbox/menu, IIRC. Make the synaptic command be "gksudo synaptic", if you've got gksudo installed. If not, you might want to install it. 

Otherwise, you can just run "sudo synaptic" in a  terminal.

---

### Post by technasma on 2006-03-31
Ok.. lots of interesting things happened!

I don't have access to a terminal in the fluxbox menu (xterm isn't showing up, can't get a console) so I installed gksu (must be the same as gksudo) to change my menu file. I used FluxConf > fluxmenu to edit my menu instead of the text file  and I got the "gksudo synaptic" command as a menu item. I ran it and now it works!!

Still can't get a terminal in fluxbox but I'm working on it... thanks for your help... #fluxbox and #ubuntu were stumped, I think they guessed it was a newb issue... thanks again!

---

### Post by technasma on 2006-03-31
I got a console.... I needed xterminal!

stuporglue, love your work.

---

### Post by stuporglue on 2006-03-31
> I got a console.... I needed xterminal!

stuporglue, love your work.

Does that mean you got stuff working? If not, let me know. There's a couple other things you could try.

---

### Post by technasma on 2006-03-31
It's all working. :)

---

