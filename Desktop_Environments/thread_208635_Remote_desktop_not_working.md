---
title: "Remote desktop not working"
date: 2006-07-03
forum: Desktop Environments
---

### Post by Presuntu on 2006-07-03
Hello,

I'm trying to remote desktop my ubuntu with my XP pro using real vnc. They both are on the same network. The remote desktop port has been opened on my router. I've turn on the remote desktop feauture in the Ubuntu preferences, 
the ping from the XP is successful, but every time the pc trys to connect it says the the connection was failed. It acts like a firewall is rejecting the vnc call from the pc.

Any idea?

Thanks

---

### Post by scxtt on 2006-07-03
there's a bit of a difference between RDC and VNC ... and i don't think microsoft's RDC program can connect to a vino VNC session ... if you're going from XP --> ubuntu, check out a VNC viewer like RealVNC ...

---

### Post by Presuntu on 2006-07-03
sorry, i've missed to mention that; I'm using real VNC from the PC side.

---

### Post by scxtt on 2006-07-03
well, the router (if you're referring to port forwarding) shouldn't matter since you're using boxes on the same network ... are you using firestarter (as a firewall - is it installed @ all?) on the ubuntu box?

---

### Post by Presuntu on 2006-07-03
[QUOTE=scxtt]well, the router (if you're referring to port forwarding) shouldn't matter since you're using boxes on the same network ... are you using firestarter (as a firewall - is it installed @ all?) on the ubuntu box?[/QUOTE]

I've done a fresh install of ubuntu 6.06 yesterday. I don't think there is any firewall in it... at least I can't find any! The vino preferences are pretty simple, i can't find any vino-server reference on my process list.. shouldn't it be running in the background?

---

### Post by scxtt on 2006-07-03
here's what i get when i have vino running (which is rare, don't like it much - i prefer x11vnc or plain-old vncserver):
[indent]:> ps -ef | grep vino
scxtt    28023     1  5 22:20 ?        00:00:00 /usr/lib/vino/vino-server --oaf-activate-iid=OAFIID:GNOME_RemoteDesktopServer --oaf-ior-fd=27[/indent]so you should have something like that if you've enabled it ... did you uncheck "ask you for confirmation"?

---

### Post by Presuntu on 2006-07-03
[QUOTE=scxtt]here's what i get when i have vino running (which is rare, don't like it much - i prefer x11vnc or plain-old vncserver):
[indent]:> ps -ef | grep vino
scxtt    28023     1  5 22:20 ?        00:00:00 /usr/lib/vino/vino-server --oaf-activate-iid=OAFIID:GNOME_RemoteDesktopServer --oaf-ior-fd=27[/indent]so you should have something like that if you've enabled it ... did you uncheck "ask you for confirmation"?[/QUOTE]

nope, it looks alike untill the "00:00:00", after that I've just "grep vino" 
Isn't it enabled by default?
Yes, I've unchecked "ask for blah blah"

---

### Post by scxtt on 2006-07-03
i'm thinking gnome starts vino as soon as you select "Allow other users to view your desktop" ... when it's checked, i see vino - as soon as i uncheck it, no more vino ... it's not "enabled by default", but it's always installed ... you just turn it on/off ...

---

### Post by Presuntu on 2006-07-03
[QUOTE=scxtt]i'm thinking gnome starts vino as soon as you select "Allow other users to view your desktop" ... when it's checked, i see vino - as soon as i uncheck it, no more vino ... it's not "enabled by default", but it's always installed ... you just turn it on/off ...[/QUOTE]

How may I turn on vino manually? What's the executable name for the server of vino?

---

### Post by scxtt on 2006-07-03
doesn't seem like you can start vino w/o using the GUI -- the only thing you can run from the terminal is "vino-preferences" which just brings up the GUI we've been talking about ... my advice would be to download **vncserver 3.3.7-8ubuntu2** from the repos and use it ... or if you're wanting to connect to :0 connections, **x11vnc** ...

---

### Post by Presuntu on 2006-07-03
[QUOTE=scxtt]i'm thinking gnome starts vino as soon as you select "Allow other users to view your desktop" ... when it's checked, i see vino - as soon as i uncheck it, no more vino ... it's not "enabled by default", but it's always installed ... you just turn it on/off ...[/QUOTE]

Thanks man, another thing: does x11vnc works with XGL/compiz?

---

### Post by scxtt on 2006-07-03
no idea - haven't ventured down that road as of yet ... i'm using a dual screen setup and i don't think XGL/compiz would be worth the configuration headache ...

---

### Post by Presuntu on 2006-07-03
[QUOTE=scxtt]no idea - haven't ventured down that road as of yet ... i'm using a dual screen setup and i don't think XGL/compiz would be worth the configuration headache ...[/QUOTE]

It was an headache to configure XGL/compiz, but when it runs it's awesome. It runs great an my old PC that was not able to run XP smoothly! (P4 1.0 Ghz, 256 mb RAM). I'm amazed how few little resources the whole linux box needs. 

I think I've read that there are some tricks to do in order to have XGL running over the dual monitor config... anyway, thanks for the help.

---

