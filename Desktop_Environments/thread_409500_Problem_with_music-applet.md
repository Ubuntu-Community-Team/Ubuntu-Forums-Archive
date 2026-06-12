---
title: "Problem with music-applet"
date: 2007-04-14
forum: Desktop Environments
---

### Post by yg17 on 2007-04-14
I installed music-applet from the repositories. I'm also using Rhythmbox. Basically, sometimes the applet will work, sometimes it won't. I have Rhythmbox running right now, yet the applet just shows the icon and not the controls, I guess it doesn't think Rhythmbox is running. But sometimes, it works fine. Any tips? Thanks

---

### Post by Aielyn on 2007-05-15
I've got exactly the same problem - I click on the applet's activation button, and nothing happens. If I run Rhythmbox by going to the menu, I don't get the controls. I suspect it might have something to do with the D-Bus, based on the fact that, if you set it to launch Rhythmbox by command instead, it works (but still doesn't provide the controls).

UPDATE: Looking at the music-applet FAQ, I saw that it says that you can debug by first running the applet in a terminal, then adding it to the panel (it then adds the one you're running from the terminal)... problem is, when I do it that way, it actually works!

As such, I have come up with a solution - First, remove the music-applet from the panel. Then, go to System - Preferences - Sessions, and click "New". Then name it something like music-applet, and type in the command /usr/lib/gnome-applets/music-applet - then go OK, close the page, and either log out/in, or press Alt-F2 and type the same command in and click OK. Then, once back in (or, alternatively, once you've run the command), add the applet back to the panel. It should work, and it *should* continue to work when you boot up next time (I have yet to test that, yet, though).

UPDATE 2: OK, I've tested it, and it works. My workaround will restore the functionality of the music-applet.

---

