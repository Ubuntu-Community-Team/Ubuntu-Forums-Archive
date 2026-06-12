---
title: "Mednafen frontend won't launch"
date: 2008-10-19
forum: Gaming &amp; Leisure
---

### Post by MEGAMANULTIMATE on 2008-10-19
Hello all,

I'm using version 0.8.9 of mednafen with 1.1.3 of the graphical frontend, mednafenfe. It was working several weeks ago (I had schoolwork so I didn't touch it for a while) and when I tried launching it I received this message via terminal:

Code: matthew@matthew-laptop:~$ mfe
location: /usr/lib/xulrunner-1.9.0.3/libxpcom.so 
before 3
Traceback (most recent call last):
  File "/usr/bin/mfe", line 6, in <module>
    mfe.MednafenFE()
  File "/home/sage/mydocs/devel/projects/mfe-0.1.0/mednafenfe/debian/mednafenfe/usr/lib/python2.5/site-packages/mfe/mfe.py", line 36, in __init__
  File "/home/sage/mydocs/devel/projects/mfe-0.1.0/mednafenfe/debian/mednafenfe/usr/lib/python2.5/site-packages/mfe/mfeutil.py", line 58, in __init__
  File "/home/sage/mydocs/devel/projects/mfe-0.1.0/mednafenfe/debian/mednafenfe/usr/lib/python2.5/site-packages/mfe/mfeutil.py", line 69, in locate
OSError: [Errno 2] No such file or directory: '/usr/local/bin'

I've tried purging and reinstalling to no avail. Using Hardy Heron with Dell M1210. Any suggestions or help would be greatly appreciated.

---

### Post by MEGAMANULTIMATE on 2008-10-19
bump

---

### Post by MEGAMANULTIMATE on 2008-10-22
Errr...no input at all? Really?

---

### Post by disturbedite on 2008-10-22
i think you'd be more likely to get a helpful response by posting this question in the mfe thread here in this forum.

---

### Post by MEGAMANULTIMATE on 2008-10-22
Ahhh...I searched and didn't find one....Okay. Thanks for the info! :D

---

### Post by rocky5051 on 2008-10-22
Here's an idea.

Go into your home folder, reveal your hidden folders (you can do this by pressing CTRL+h in GNOME or Xfce desktops, or ALT+. in KDE desktops), then go to the ".mednafen" folder, and inside that folder you will find a mfe.ini file.

Delete that file, and try it again. It might just be a bad setting...or you could have accidentally removed a dependancy. In which case, if mednafen itself still runs, just type this command in:

```
mednafen /path/to/your/game
```

Hope that helps.

---

### Post by MEGAMANULTIMATE on 2008-10-24
Well, I got mednafen to work via the command line. Sorry, but your suggestion didn't work. I guess I could keep using mednafen this way...but I hate command-line operated programs. Could there be another way to fix this?

---

### Post by MEGAMANULTIMATE on 2008-10-25
bump

---

### Post by FranMichaels on 2008-10-25
Just right click your rom, choose open with, then custom command, type mednafen. There. Next time you double click, it will just launch the game.

---

### Post by MEGAMANULTIMATE on 2008-10-27
That's a pretty effective workaround, and I thank you for it. But is there any way to fix mednafenfe? It troubles me that I haven't received any other info on how to correct this problem.

---

### Post by wingnux on 2008-10-27
You may try to install some python-related packages, it always works for me when I get those kind of crashes.

Yeah, I really do install some random python packages :P

---

### Post by MEGAMANULTIMATE on 2008-10-27
Heh, knowing myself, I think that would do more harm than good. What about the terminal error message I provided? Does it not tell anyone what went wrong?

---

### Post by Dodongo Dislikes Smoke on 2008-11-25
Did you by any chance try out an e17 install script?  I'm getting the exact same error, right down the the "/home/sage/" part, and ending with "OSError: [Errno 2] No such file or directory: '/opt/e17/bin'"

---

