---
title: "Separate xSessions, ONE monitor."
date: 2009-02-25
forum: Desktop Environments
---

### Post by Redsandro on 2009-02-25
Hi,

I was wondering if I can configure (x)ubuntu in a way that I have two x sessions. Same layout and everything, but just two separate. (ctrl+alt+F7/F8 or something).

See, I have one autologin, but I'd like to have another session hidden under the function key where I can login as another user, without the autologin to fire.

This saves me a lot of clicking and switching trouble when I quickly want to do something gui with the other user.

When I search for this, topics come up about dual monitor layouts where people want different monitors to behave like different computers. That's not what I want. I have one monitor layout that I want to keep the same.

---

### Post by x1a4 on 2009-02-25
Hi,
It [this]("http://hex1a4.net/xubuntu/howto/03/") what you're looking for?

When making your changes make sure you have the following in /etc/gdm/gdm.conf-custom
```

[daemon]
AutomaticLoginEnable=true
AutomaticLogin=*username*

```

---

### Post by Redsandro on 2009-02-27
Thanks, that's about exactly what I wanted!

However, even though I did exactly what it said, after a quick flash of a text tty login screen, the monitor goes "no signal" and not a single one of ctrl-alt-f1..f12 works anymore.

I hope it didn't break the recovery mode as well or I'm gonna have to build a cd player in there to boot the liveCD for recovery.

I guess that guide is not compatible with Xubuntu 8.10.

---

### Post by Redsandro on 2009-02-28
I lied. I restored an image and tried again, and it sort of works now. So I must have done something wrong. I guess I screwed up either mixing a capital letter with a small letter or by not leaving blank lines in gdm.conf-custom. Not sure.

Anyway, the autologin is consistently going to TTY1 now. The X servers for TTY6 and TTY7 are on TTY5 and TTY6. TTY1 is also in 256 colors while the rest is in 24 bit colors.

---

### Post by Redsandro on 2009-03-08
bump

any thoughts on how to make this work in x8.10?

---

### Post by Jose Catre-Vandis on 2009-03-08
Try this (you might need to undo what you have already done, or look at a different tty)

```
CTRL+ALT+F1
```
login with user and pass
then type this:
```
startx -- :1
```
then
```
CTRL+ALT+F9  <-- this is the default
``` or whatever your first free X session tty is
You should get a gui screen.

I did this on my Xubuntu 8.10 and it worked after a fashion, but most of my desktop settings (background, panel locations, icons etc) were not present. But I had a working desktop.

See this post on the forum:
[http://ubuntuforums.org/showthread.php?t=185555](http://ubuntuforums.org/showthread.php?t=185555)
and to really big it up, check out bohdi's howto here:
[http://ubuntuforums.org/showthread.php?t=271674](http://ubuntuforums.org/showthread.php?t=271674)

---

### Post by Redsandro on 2009-03-08
Thanks for the input, but I just get X - with the X mouse cursor. absolutely nothing is present. I like to do GUI stuff like login at least, and it would be okay if my settings (like desktop) are gone. But now 'everything' is gone. :P

I'll try and see if I can understand the scripts from the second link you provided so I could tweak them just to start another similar session. Thanks for the link.

---

