---
title: "More KDE4 white/black screen of death"
date: 2009-03-26
forum: General Help
---

### Post by dmeehl on 2009-03-26
I know this subject has come up several times but there doesn't seem to be a resolution to it as of yet aside from removing the .kde4 folder (which didnt work for me). Hopefully I can help shed some light on what is going on and maybe someone can suggest something that might work.

This is how it went down for me:
I started with ubutu 8.10 and installed kde4.1. Then I upgraded to kde4.2 when it was released. Everything worked fine for many weeks. I leave my computer on 24/7 most of the time and it had been a couple of weeks since my last reboot. I noticed that some of the icons in the task bar were no longer showing up, but the text was. A short while later Plasma crashed and my desktop went away completely (desktop, plasma, widgets, background). My currently opened application windows stayed. Since I was in the middle of copying some files to an SD card using Dolphin, I let the copy finish before I used a keyboard combination to bring up the logout button. I rebooted the system using the logout screen.

Upon startup the login manager appeared and I logged in. After the kde spash screen, I got just a black screen with a cursor. On subsequent logins the splash screen does its thing, then I get the default wallpaper, later the synaptic bubble telling me there are updates appears in the top left corner, I assume since there's no systray for it to locate to. After that bubble disappears, I just get a blank white screen with the cursor. The only input reaction I can get from here is to use CTRL+ALT+BKSP to kill x-server, or CTRL+ALT+# to change to a terminal. No other key combinations or mouse clicks do anything.

The difference in my case appears to be that I haven't changed anything. I didn't update or install any software as it seems most others with this problem had. It appears that Plasma just crashed and as it did (or when I logged out of KDE afterwards) altered something that is preventing me from logging in.

I've tried removing .kde and .kde4. I tried using the xfix option in the recovery console, but this doesnt appear to be an X problem. The login manager works fine.

I also tried creating a brand new user. When I try to login using the new user, the KDE spash screen doesnt even show up. It just hangs showing only the background.

Ok, so that's basically all I've got. Does anyone have any suggestions?

---

### Post by kuja on 2009-03-26
Wow, that's not good. One potential idea is to upgrade to KDE 4.2.1 (or if you already have, go back to KDE 4.2). Next, I'd say dist-upgrade to get *everything* up to date. 
If these things fail I don't know what to say, except that in one month you'll have a new release to try out and hopefully it won't experience the same problem(s).

---

### Post by dmeehl on 2009-05-26
FYI, this worked. Thanks for the suggestion.

---

