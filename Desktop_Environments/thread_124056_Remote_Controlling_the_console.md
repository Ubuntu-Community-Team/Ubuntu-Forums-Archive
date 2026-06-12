---
title: "Remote Controlling the console"
date: 2006-01-31
forum: Desktop Environments
---

### Post by plazman30 on 2006-01-31
I set up Breezy Badget and installed FreeNX with it and I love the speed I get.  Truly amazing.  The only thing I am trying to do, is grab control of the console.  So, if I log in to my PC at home and fire up, say a Bittorrent client and start downloading some Linux ISO images, I can use NX (or VNC or some other tool), to grab that same display and let me see my running bittorrent client.

At present, NX starts a whole new display when I log in remotely.  And if I log in remotely, and then login at home, I also get a different display.

Is there some way to keep the same display regardless of where I am logging in from?

Andy

---

### Post by cwaldbieser on 2006-01-31
[QUOTE=plazman30]I set up Breezy Badget and installed FreeNX with it and I love the speed I get.  Truly amazing.  The only thing I am trying to do, is grab control of the console.  So, if I log in to my PC at home and fire up, say a Bittorrent client and start downloading some Linux ISO images, I can use NX (or VNC or some other tool), to grab that same display and let me see my running bittorrent client.

At present, NX starts a whole new display when I log in remotely.  And if I log in remotely, and then login at home, I also get a different display.

Is there some way to keep the same display regardless of where I am logging in from?

Andy[/QUOTE]

I am not sure if this helps, but I think if you run vncserver from your desktop as a normal user before you leave, you can VNC into your actual session.  You'll have to set the port to be something other than the default if you have another VNC server running.

---

### Post by awi on 2006-01-31
If your application works on the console (terminal), you could use the [COLOR="SeaGreen"]screen[/COLOR] program, a must have tool (IMHO), for remote woking (ssh) on a unix box. :)

---

### Post by plazman30 on 2006-01-31
I have used screen before and it is a truly awesome program.  The programs I am talking about here are full Gnome apps sadly.  Those are the ones I would like to be able to acces remotely once I launch them locally.

I would also prefer to use NX, since it's much faster than VNC is.

Andy

---

### Post by awi on 2006-01-31
I've never used freeNX, but have you tried to do the same way as you do with screen? I mean, starting from your "physical" session, I mean when you are in front of your pc, a freeNX session, and starting there the programs you would like to monitor later? I use to do this with VNC, on my desktop I start a VNC session, from the same machine start my p2p aplications and later from outside the office, connect to my vnc to check for the status.

---

### Post by plazman30 on 2006-02-01
Well, I should have to start a VNC session from ini front of the PC.  I may fire up and app, or leave Thunderbird running by accident and then NX into the box and am unable to access these apps.

---

