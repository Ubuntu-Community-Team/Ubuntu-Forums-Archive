---
title: "weird border glitch on maximized windows since latest update in 12.04"
date: 2013-01-30
forum: Desktop Environments
---

### Post by bogdarnet on 2013-01-30
Only noticed this since today's update... a weird one-pixel border at the top of maximized windows... can see it in firefox when a page refreshes, then it disappears.  

It's an irritating glitch in the GUI, any idea how I can make it stop?  

Thanks in advance.

---

### Post by bogdarnet on 2013-02-01
Another detail I've noticed about this... the border pops up on the top and left sides of maximized windows when switching from one tab to another... it's not just firefox, can do it in Gedit also.

Wouldn't be so bad if it were a plain, one-color border (well, it'd still be kind of irritating), but the border has three or four colors in it.

No one else sees this thing?

---

### Post by bogdarnet on 2013-02-01
Another detail I've noticed...

this occurs under Unity 2D.  When I switched to 3D, it went away.  (Of course, there was some reason I switched to 2D quite a while back, which I'll probably rediscover soon...)

---

### Post by bogdarnet on 2013-02-07
P.S. Tried to do a screen capture of it, but the line disappears when I press "print screen"...

Anyone else noticing this!?

---

### Post by bogdarnet on 2013-02-07
Okay, got a picture of it...

---

### Post by bogdarnet on 2013-02-07
Tried using gconf-editor to turn on:

/apps/metacity/general/compositor-effects

But it's still there.  Other failures have included:

unity --reset
Turning off "window decoration" in ccsm

and lots of other things I took inadequate notes on...  

Thinking of reinstalling, though I hate to do that for this one little line...

---

### Post by bogdarnet on 2013-02-07
Hello?!?

Is anybody out there?

If so, can you at least confirm or deny you see the same border glitch when using Unity 2D???  

(The most reliable test looks to be starting a gedit session, making a new tab.  It always appears on this machine in that case.  Under firefox, it often appears while switching tabs, but sometimes then disappears.)

Most recently, just to check, I made a new user which did have the same problem under Unity 2D on this machine.

---

### Post by bogdarnet on 2013-02-07
Solved?  (Not sure this is a good solution yet, really though...)

Tried compiz --replace to dump metacity (still in Unity 2D though)...

The glitch is gone.  But now other strange things happening, like the terminal button in unity launcher not going back to an open terminal, but only opening a new one.  (The other launcher buttons, like firefox and gedit, do seem to go back to the open ones.)

And reportedly compiz and unity2d aren't that good together.

But at least the line is gone.

---

### Post by bogdarnet on 2013-02-07
Okay, fixed that and a couple other things (dash wasn't working, for example), by following these steps from:

[http://askubuntu.com/questions/130443/how-to-run-compiz-on-unity-2d-ubuntu-12-04](http://askubuntu.com/questions/130443/how-to-run-compiz-on-unity-2d-ubuntu-12-04)

gksudo gedit /usr/share/gnome-session/sessions/ubuntu-2d.session

Changing metacity to compiz
saving and exiting gedit
sudo restart lightdm
and logging back in

so far, things look good

---

