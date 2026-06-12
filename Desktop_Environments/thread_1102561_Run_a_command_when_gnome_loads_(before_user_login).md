---
title: "Run a command when gnome loads (before user login)"
date: 2009-03-21
forum: Desktop Environments
---

### Post by KyferEz on 2009-03-21
I've got a command I need run before gnome loads, but I'm confused about a few things reading the man pages for update-rc.d. I don't understand what it means when it says that admins shouldn't use it to manage runlevels. And what is all this about links?

My command: /usr/bin/xgamma -rgamma 0.73 -ggamma 0.40 -bgamma 0.88

I've spend almost 2 hours trying to get this command to run at startup using the System->Sessions window cause it took forever to figure out that Ubuntu did not like "> /dev/null" at the end of the command for some reason. I finally got it running without that part, but in the end that method sucks because the colors are off on the login screen, so that's why I'm looking into update-rc.d.

Anyway, I'd appreciate a better explanation of update-rc.d and runlevels than the man pages gives, and also an explanation why the autorun setup didn't like the "> /dev/null" in the command so hopefully I can get it working before gnome loads and learn a few things in the process.

---

### Post by KyferEz on 2009-03-30
noone?

---

### Post by Paddy Landau on 2009-04-01
I think that this may be what you're looking for.

Read sections 9.3 and 9.4 carefully.

[http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit](http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit)

Give it a try.

In short (as I understand), you'll want to create a file in directory [COLOR=Navy]/etc/init.d[/COLOR] (let's say you call it *gamma*) that contains the following:
```
#!/bin/sh
echo -n Starting gamma...
/usr/bin/xgamma -rgamma 0.73 -ggamma 0.40 -bgamma 0.88
echo Done.
```Set the permissions:
```
sudo chmod +x gamma
```Test the script before proceeding!

Then register it to run.
```
sudo update-rc.d -n gamma start S .
```Note two things:

[LIST=1]
[*]There is a "." at the end of the line.
[*]The [COLOR=Navy]-n[/COLOR] option indicates a test (a "dry-run"); update-rc.d will simply tell you what it would do, so it's safe to try. If you're happy with what it reports, then run it for real by omitting the [COLOR=Navy]-n[/COLOR] option.
[/LIST]
Let me know if it works, I'm curious.

---

