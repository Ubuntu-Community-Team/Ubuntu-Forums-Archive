---
title: "change krunner default (kde3 konsole --&gt; kde4 konsole)"
date: 2008-06-13
forum: Desktop Environments
---

### Post by psquared89 on 2008-06-13
How do you change the krunner default?  This isn't really that important, it's just annoying to occasionally open the wrong konsole.

For whatever reason, krunner gives higher precedence to "Konsole/KDE3 (Application)" than "Konsole (Application)".  If I type the whole word konsole, it switches over to "Run konsole (Command)", which will load the kde4 konsole; if I hit enter a key too soon though, it will choose the kde3 konsole.  I'm assuming the only reason that's even installed is for legacy support for some applications (ie, embedded konsole in kate? I don't know, just guessing) - I don't really care, I would just like to change the krunner default.

Running Kubuntu 8.04 w/ kde4

---

### Post by Zorael on 2008-06-13
Conjecture: when you hit enter early, it runs the command as is ("**konsole**"), which launches the program konsole: Konsole/KDE3. KDE4's Konsole is 
*named* **konsole-kde4**, and it only defaults to it once it has had time to match what you wrote to its defaults.

One way is to examine the contents of your [FONT="Courier New"]~/.local/share/applications/konsole.desktop[/FONT]. What does it point to? konsole or konsole-kde4? If konsole, change it to konsole-kde4 and see if it does anything.

Another way is to *rename* your konsole file in /usr/bin/ to konsole-kde3, then make a symlink to konsole-kde4. This'll make it always run KDE4's Konsole though, even if in KDE3, unless you write some nifty script that determines your current environment and launches the proper app.
```
$ sudo su
# cd /usr/bin
# mv konsole konsole-kde3
# ln -s konsole-kde4 konsole
```
This is all assuming konsole-kde4 is located in /usr/bin/, but I find it difficult to imagine it shouldn't. This command should find it for you.
```
$ locate bin/konsole-kde4
```

---

