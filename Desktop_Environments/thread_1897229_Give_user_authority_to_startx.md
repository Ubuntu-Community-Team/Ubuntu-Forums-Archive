---
title: "Give user authority to startx"
date: 2011-12-18
forum: Desktop Environments
---

### Post by BlackWidower on 2011-12-18
So I have a server running Ubuntu that I tried installing a GUI on.  LXDE to be precise.  My goal here was to use as few packages as possible to get a lightwieght OS, leaving more room for media.  So I installed the minimal components, lxde-core and initx, and ran startx.

I think you know what's coming.  

> X: user not authorized to run the X server, aborting.

Natch.  So I tried using xauth to get full authorization for the required user using the following command...

> generate :0 . trusted

...and I get another error.

> unable to open display ":0".

Of course I can open the display using root in another session, and it appears to work fine, as I get the following message:

> authorization id is 265

...doesn't look like an error.  But when I start X server using my user account, I get the same old error.

> X: user not authorized to run the X server, aborting.

Now, of course I could just install lxdm and start X that way.  But I don't want to do that for two reasons.  One, I'll have to log in through vnc every time I reboot, which is annoying; and two, it means I'll need to run X all the time, even when I don't need it.  Which is a waste in my mind.

So here's my question: How do I give a user authority to start X?

It seems like it should be a pretty simple task.  But it appears not.  Am I using the wrong command?

---

### Post by JC Cheloven on 2011-12-18
> **BlackWidower said:**
> So I have a server running Ubuntu that I tried installing a GUI on.  LXDE to be precise.  My goal here was to use as few packages as possible to get a lightwieght OS, leaving more room for media.  So I installed the minimal components, lxde-core and initx, and ran startx.

I assume you mean lxde-core and xinit.
I think none of them has xorg as a dependence, which would be a problem. So please, if you didin't, try ```
sudo apt-get install xorg
```
reboot and see what happens. 

Also, I think you may miss some tools that aren't heavy at all. Obconf among them. I'd install it also.

Hope this helps

EDIT: are you really on 8.10 interpid ibex? I think it's unsupported, and no repos available...

---

### Post by BlackWidower on 2011-12-19
Well, that didn't work.  I don't know what your underlying idea was, because I know I could startx as root.  The problem is: I can't startx as user.

Of course, I did notice a new error.  

> No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..

It does this ad infinitum.  I just noticed a similar error from authx as well.  Anyway, I think it's a step in the right direction.  If I know what protocol it's talking about, I might be able to send the right command to authx and get the authorization.

This shouldn't be this difficult.

Oh, and thanks for pointing out xorg to me.  I was looking for a package like that.

Oh, and no, I'm not on Intrepid, I'm on Ornery.  But for some reason I don't have permission to access the "Edit Your Details" page.  It says I need to make 50 posts.

---

### Post by JC Cheloven on 2011-12-19
I had the hope it worked that way. I'm afraid I'm not experienced enough (or at all) in servers to help you further. Well, at least I bumped your thead LOL. Anyway, I still think your problem must be a missing package. 

Only thing I can suggest at this time is to have a look on the community documentation [on the subject]("https://help.ubuntu.com/community/ServerGUI").

EDIT: oh, [this page]("https://help.ubuntu.com/community/Installation/LowMemorySystems") about building from a minimal command-line install should also be useful. I know there are differences among a server install and a command-line desktop install, but the process of adding a DE should be very similar.

JC

---

### Post by BlackWidower on 2011-12-19
Found a solution, by running: > sudo dpkg-reconfigure x11-common I can give authority to all users to startx.  I don't think I can give authority to individual users.  But I don't mind.  This works.

---

