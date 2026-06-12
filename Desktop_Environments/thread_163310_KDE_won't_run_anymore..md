---
title: "KDE won't run anymore."
date: 2006-04-20
forum: Desktop Environments
---

### Post by arachn1d on 2006-04-20
Well not properly.

I'm now typing in windows.

I am not sure what happened. I was trying to install an osx like startbar from karamba. Anyway, I ended up restarting the laptop and now kde loads, but nothing works. It's like a blank session. I try start a new one but the same thing happens.

Any idea, or do I just reinstall all together?

---

### Post by GoldBuggie on 2006-04-20
I don't know what is wrong but when I reach these kind of problems I always goto konsole and check the log files in /var/log/ (kdm, messages, dmsg, X etc) From there you will probably see what the problem is.

Also...if you want to check these files in graphical mode then logging in thrue konsole mode and typing startx might start your kde session.

---

### Post by jetpeach on 2006-04-20
It's hard to help because I'm not sure how much you've tried or what version of KDE your running etc, but here's some possible help.

Have you tried control-alt-backspace to restart the X session once your in KDE?
Can you get to a terminal after it loads (control-alt-f3 or any of the function keys up to f7 which is kde terminal).

Never used karamba or anything, but you shouldn't have to reinstall, although it might be the easiest.  You could try just uninstalling kde and reinstalling it, perhaps the latest version, search kubuntu.org for kde 3.5.2 and there are instructions to update it.

---

### Post by louis_nichols on 2006-04-22
[QUOTE=jetpeach]It's hard to help because I'm not sure how much you've tried or what version of KDE your running etc, but here's some possible help.

Have you tried control-alt-backspace to restart the X session once your in KDE?
Can you get to a terminal after it loads (control-alt-f3 or any of the function keys up to f7 which is kde terminal).

Never used karamba or anything, but you shouldn't have to reinstall, although it might be the easiest.  You could try just uninstalling kde and reinstalling it, perhaps the latest version, search kubuntu.org for kde 3.5.2 and there are instructions to update it.[/QUOTE]


What I would do, when nothing else works anymore, is

```
rm -rf ~/.kde/
```

this should return kde to zero. Tweaking superkaramba shouldn't mess anything fundamental about your kde installation, since, not being root, you don't have write permissions on its binaries and config files.

---

