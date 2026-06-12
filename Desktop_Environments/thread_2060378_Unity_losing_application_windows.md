---
title: "Unity losing application windows"
date: 2012-09-20
forum: Desktop Environments
---

### Post by upnix on 2012-09-20
Running Ubuntu 12.04 with Unity. Using the fglrx video driver.

Way too frequently I'll be in a desktop (say, #2), and I'll want to go back to Firefox (or gedit, or KeePassX). So I go over to the panel, click Firefox and .. nothing. So I go looking for my Firefox window, and it's half in desktop 4, half off the bottom of the screen.

Now, the expected (and often ocurring) behaviour is that when I click on the launched application icon, it moves me to the desktop that window is in. Except 30% of the time, that application window ends up in another desktop, and I have to manually go find it.


Anyone seen this before? Know of a fix? It's done it for as long as I've been running 12.04, but it's finally to that point where it's got to stop.


Thanks,
Chris

---

### Post by trev mesh on 2012-09-20
I get a similar problem with gimp and LibreOffice (see my previous post). The only 'fix' I've found is to select Ubuntu 2D at the login password prompt. May be this would work for you? It's less attractive but otherwise I've not so far seen any other difference to the 'proper' desktop.

---

### Post by markbl on 2012-09-20
I like Unity but my biggest criticism has always been that it is very buggy. I have not seen the specific bug you describe but I have seen others very much like it. All I can suggest is to make sure your system is updated, then reboot, do a "unity --reset", and reboot again. I find that if you choose esoteric settings in Compiz then you are more likely to see these odd problems.

Other than that, I actually now mainly use Gnome Shell which I prefer over Unity and certainly find it has always been rock solid reliable.

---

### Post by upnix on 2012-09-26
For anyone who is curious, the fix to the problem I described was to disable the auto-hide feature for the launcher bar.

Having said that, I still have various other little problems (ALT+Tab changing the view, but not actually the window focus), but this is good enough for now.

Thanks for the help. The Unity settings reset is how I discovered this.

---

