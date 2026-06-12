---
title: "I did something really, really wrong."
date: 2012-11-27
forum: Desktop Environments
---

### Post by Athena's Owl on 2012-11-27
So I bought a new netbook and I ripped Windows 8 off it and installed Ubuntu. Yay! But i felt that the environment was really, frustratingly slow.

When I installed i had it automatically log me in, no password required, because no one is going to touch this netbook but me. so it doesn't ask me for a password, it just logs straight into ubuntu 12.10.

I installed another desktop environment because i heard it was faster, if not as pretty, but i don't want to sit around waiting for programs to open.

but I couldn't figure out how to switch - because when i log in, it doesn't ask me for a password. And then i thought, "oh, I'll just log off, and see what happens."

you guys have heard of an onosecond, right? It's important. Because I had one. I chose the wrong desktop enviornment. I meant to choose LXDE, but there were two more environments there that I hadn't heard of, and I didn't really look at the names, and i chose one of them by accident.

Now I have nothing. NOTHING. I have a gray screen and a mouse pointer, and no desktop environment at all. I have no idea what this is. And I can't escape it, because...I foolishly didn't set my netbook to make me log in, so it automatically logs into the environment that was last set. which is this gray blankness with a movable mouse arrow. And I was going to leave to go on a writing meeting that starts in two hours and I have no idea what I have done. Curse it! Can *anyone* help?

I'd use the boot stick that I used to format and install ubuntu...but I don't *have* it. I lent it to a friend, permanently. yesterday. by mail. and I don't have any more USB sticks.

I really blew it this time.

---

### Post by lykwydchykyn on 2012-11-27
You probably have logged in to Openbox, which is the window manager portion of LXDE.  

If you right-click on the desktop, do you get a popup menu?

---

### Post by Athena's Owl on 2012-11-27
I do! So this is OpenBox?

---

### Post by LewisTM on 2012-11-27
Press Alt-SysRq-K all at once. This should kill the X server and return you to the login screen.

Good luck!

---

### Post by dannyboy79 on 2012-11-27
hit ctrl-alt-f1, login to the tectual environment then issue the following command, I believe this should get you back to where you can choose your desktop manager
```
sudo service lightdm restart
```

---

### Post by lykwydchykyn on 2012-11-27
> **Athena's Owl said:**
> I do! So this is OpenBox?

Yes.  It's pretty minimal, but you should be able to log out and change your session from the menu there.

---

### Post by Athena's Owl on 2012-11-27
Okay, I got it! I did it kinda ugly but once I got a command line window I used the -KILL -u command, and i'm in LXDE now. It's REALLY FAST. I like it a lot! I messed around a bit with Open Box once I realized what right click does, and that too is cool. You saved my writing meeting. Thank you so much.

---

