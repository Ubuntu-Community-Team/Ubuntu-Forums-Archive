---
title: "menu problems"
date: 2008-02-26
forum: Desktop Effects &amp; Customization
---

### Post by phoenix5002 on 2008-02-26
Here is what the bars on top and bottom of my screen currently look like:
[http://img352.imageshack.us/img352/7167/desktopgf7.jpg](http://img352.imageshack.us/img352/7167/desktopgf7.jpg)

notice how the firefox, evolution, and help icon aren't next to the menus on the left anymore, now they are on the other side.  Also, the username "Jason" appears all the way to the right instead of to the left of the desktop applet like it should.
But the biggest annoyance is on the bottom bar,  My trash bin is in the middle instead of all the way to the right.  This isn't good because now it's sort of like the size of my task bar spans from the left to the middle, if I open new programs they will all be fit inside that area, so theres all that other space (from the trash to the right) that I can't use.

That's the problem, now here's what I think caused it just in case it might help somehow.  I was launching PlaneShift (the game) and when it was loading it suddenly crashed and didn't revert my desktop resolution back to 1280x800 it was still stuck at 640x480.  I kept trying to change the resolution but when I would select 1280x800 or any other it would show the "keep settings?" dialog but the resolution wouldn't actually change.  So after trying that I restarted the Xserver and it still loaded into 640x480, but this time I could change the resolution back to 1280x800, however I noticed that the trash bin was now messed up.  I then restarted my computer and it was the same, so I tried changing back to 640x480, then going back to 1280x800, and that resulted in my desktop being in its current state.

---

### Post by jhenager on 2008-02-26
Have you tried unlocking the icons and dragging them back to where you want them to be?

---

### Post by phoenix5002 on 2008-02-27
ok, I just tried that and I had some success but a few items won't let me move them.  For example when I try to move the trash even though I click and hold it will still open the trash folder and the icon doesn't move when I drag it.  I got the 3 icons (firefox, evolution, and help) back to where they should be, but that was pretty much it.

Also, I'd like to add that ever since this problem occured (before I tried moving them myself) every time I would turn on my laptop the top bar would have a different arrangement.  I could fix it though if I were able to move all the icons but some won't let me.

I was hoping there would be a way to just reset the menu items back to the default.

---

### Post by phoenix5002 on 2008-02-27
I fixed it, I found this:
[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

just deleted the folders it said, then restarted and everything was back to normal. :)

---

