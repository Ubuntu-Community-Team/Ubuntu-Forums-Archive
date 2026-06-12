---
title: "Is there a way to disable the &quot;clock&quot;/notifications lock screen?"
date: 2019-05-30
forum: Desktop Environments
---

### Post by kpatz on 2019-05-30
In 16.04 (Unity), when the screen locks, it goes directly to a screen with the password prompt.  To unlock, I type in my password, hit enter, done.

In 18.04 and 19.04 (Gnome), the screen locks to a page with a clock on it, and notifications if any.  I have to then hit enter, or click and drag "up" with the mouse to get rid of this page and get to the password prompt.

I find this an annoying extra step.  If I want to use the lock screen for security, it's an extra click/drag or key to hit before I can enter my password and unlock the desktop.  Is there a way to turn this off and just have it go directly to the password prompt page like in 16.04?

---

### Post by mc4man on 2019-06-02
It seems that's the way Gnome's (gnome-shell)  lock screen works. I'd think your option is,

Go to settings > privacy > Lock Screen,  turn automatic lock screen off. (and maybe the rest.
Then just use binding to lock, i.e, super+L  This should  briefly show the lock screen & then blank the screen. A button press will bring to password screen.
(- note that any button pressed is entered in password box so either use the enter key or just start typing password. A mouse movement seems to open the orig. lock screen..

---

