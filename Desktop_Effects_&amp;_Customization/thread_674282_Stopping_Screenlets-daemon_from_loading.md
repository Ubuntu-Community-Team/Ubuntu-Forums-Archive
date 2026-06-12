---
title: "Stopping Screenlets-daemon from loading"
date: 2008-01-21
forum: Desktop Effects &amp; Customization
---

### Post by rune0077 on 2008-01-21
I decided to try out the Screenlets just yesterday, but I really need to know how to stop the Screenlets-daemon from loading at startup, because I don't plan to use that often.

I realize that I can just not have any screenlets running at startup, but this is not what I'm after. I want the daemon to not start at all, and for the Screenlet manager to only be active when I trigger it. Is this doable? I've removed the entry from the autostart-folder, but this hasn't stopped it at all (Screenlets still activate themselves at startup if I set them to it, which they shouldn't if the daemon isn't running).

---

### Post by FuturePilot on 2008-01-21
The only thing I can think of is to make sure there's nothing in your Sessions dialog (System>Preferences>Session) for Screenlets. I'm not sure why it would be autoloading. It doesn't do that for me.

---

### Post by rune0077 on 2008-01-21
Did that too. No luck. There's nothing in sessions I can associate with Screenlets at all. Even weirder, I did something (not sure what(, and now the Notes screenlet *always* launches at startup. It's not in sessions, it's not in autostart, and strangest of all, the "autostart on login" isn't even ticked in the manager. Yet, it loads up every time, which is starting to get rather annoying.

---

### Post by Whise on 2008-01-21
the deamon loads everytime , only this way you can see it in the tray , however if it bothers you i will add an option to make it not visible

---

### Post by rune0077 on 2008-01-22
So it wouldn't be possible to *prevent* it from loading? Ah, I guess I can live with that, as long as it stays out of my business :) Currently, the stupid notes still keep autloading on startup, though, which is getting bothersome. I tried just deleting the note screenlet, which did the trick, but naturally it got reinstalled with today's update.

So the next question is: is there a place, besides autostart, sessions and currently running screenlets, where information about what screenlets load at startup are stored. 'coz the notes are nowhere to be found in any of these, and they still *do* start up, even after being deleted and then reinstalled?

---

