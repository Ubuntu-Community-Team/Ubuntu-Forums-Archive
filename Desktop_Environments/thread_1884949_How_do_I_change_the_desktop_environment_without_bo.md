---
title: "How do I change the desktop environment without booting?"
date: 2011-11-22
forum: Desktop Environments
---

### Post by megamasha on 2011-11-22
I think this should be a fairly simple problem to fix for someone who knows how.
If you don't know how to do it, please tell someone about this thread, who you think might know!

So, here's the story:

I have kubuntu 11.10.
I installed the 'ubuntu-desktop' package just to try out unity.
I tried unity. It's OK, but I much prefer KDE.
I logged out, about to log back into kde, but when I looked at the list of available desktop environments, I noticed 'metacity'.
I wondered 'what's that? Let's try it.'
I logged in and nothing happened. I had a mouse cursor, and the login screen background. That's all.
I left it for a while.
Nothing happened. No keyboard response, no right-click, nothing.
So I reset my machine.
When it booted back up, I get no log-in screen, no background, just a blank screen and a mouse cursor.
This happens every time, making my kubuntu installation unusable.

I'm assuming it's trying to log back into matacity each time, and encountering the same problem.

My question is: How do I get it to log back into kde upon next boot?

I am writing this using a lubuntu live USB stick on the same computer, so I have access to the hard drive and I imagine I can change config files - I just don't know which one decides which desktop environment to load.

My default desktop manager is kdm

---

### Post by megamasha on 2011-11-22
I found an alternative solution (but I'd still like to know where this config option is in ubuntu) -

boot up (ends up on a blank screen with mouse cursor),
load a tty session (Ctrl + Alt + F1),
remove metacity (sudo apt-get remove metacity)
reboot (sudo reboot)

Upon next boot, x server can't find metacity and switches to default.

I'd still like to know where this config option is in ubuntu.

MM

---

