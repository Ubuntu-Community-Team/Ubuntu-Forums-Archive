---
title: "Controlling which display apps open on"
date: 2010-01-29
forum: Desktop Environments
---

### Post by Objekt on 2010-01-29
Is there a way to control which screen an application window opens on when started?  Lately this has been driving me nuts, in that some apps open on my primary screen, some on the secondary, with no apparent pattern.

It's especially irritating because I have my two monitors arranged so that you can't see one when sitting at the other.  I use a 21" CRT for the primary display (Gnome panel and desktop shortcuts are there) and a 24" LCD for the second monitor.  I use the LCD exclusively for watching movies.  When an app window opens there instead of the CRT, I have to get up, walk across the room, and use the wireless mouse there to move app windows back to the main display.

FWIW, my video card is an Nvidia 9800 GTX+, I am using the Nvidia drivers (version 190.something), and I have Xinerama turned on.  Ubuntu version is 9.10 64-bit.

---

### Post by Objekt on 2010-02-02
I don't believe I'm the only one to ever have this problem.  Doesn't anyone have any ideas how to fix it?

---

### Post by artheus on 2010-02-02
I believe this is controlled by the application itself. Some of the applications save their x and y positions on the screen, when you shut down the program.

I had similar problem earlier with some program. Which couldn't save it's position because it was not run as su. So try to open program as su

```
sudo *program_name*
```

And shut it down again, and check if it saved the position.

Cheers,
Artheus

---

### Post by NarcT on 2010-06-07
You could install Compiz or Advanced Desktop Effects Settings and go to Place Windows.  Click the tab Fixed Window Placement and now you can specify which screen or exactly how they open.

---

