---
title: "UT2004 Demo crashes XServer"
date: 2006-12-01
forum: Gaming &amp; Leisure
---

### Post by sgardne on 2006-12-01
Hello,

This is my first attempt at gaming on Linux, and I'm having a bit of a problem. I finally got the non-corrupt version of the ut2004 demo and got it installed, but now every time I try to run the game, it crashes my xserver and bumps me back out to the login screen. Are there some log files I should be looking at?

Thank you.


edit: I should also mention that the only time I can get anything at all to happen is if I run the game as root. Running as local user gives me an error about not finding some file in a configuration. I've chown'd the executable and all the files in /usr/local/games but it doesn't seem to have had any affect.

-s

---

### Post by Tuna-Fish on 2006-12-01
_***Don't***_ run games as root.

Actually, I'd ever propose installing it as user - just run the installer without sudo, and place it all in /home/(yourhomedir)/games/u2004 or something.

But for the actual problem, what GPU and drivers are you using?

---

### Post by Tuna-Fish on 2006-12-01
Oh by the way, the only files the game needs to write to during play are in ~/.ut2004 so no need to chown anything from /usr/, just make sure ~/.ut2004 is writable for you.

---

### Post by sgardne on 2006-12-01
Thank you for your reply. The crashing was due to a bug in the current nvidia drivers. I fixed it by upgrading to the latest beta version.

I will check on the folder permissions in the morning and see what's what. Thanks again.

-s

---

