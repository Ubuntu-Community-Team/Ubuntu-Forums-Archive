---
title: "Installed Steam, but won't launch in wine"
date: 2006-10-12
forum: Gaming &amp; Leisure
---

### Post by kirkio on 2006-10-12
I installed Steam on wine via the instructions at this website:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games)
I am running Wine version 0.9.9

The installation had a problem crashing at 26%, but it is a common problem and I ran the fix for it, and then it successfully installed.

So, I do the command to launch Steam.exe:
```

kirk@kirk-laptop:~$ wine Steam.exe
wine: could not load L"c:\\windows\\system32\\Steam.exe": Module not found

```
oops, I need to be in the Steam directory
```
kirk@kirk-laptop:~$ wine ~/.wine/drive_c/Program\ Files/Valve/Steam/Steam.exe
```
At this point, nothing happens. No errors, no program launching.
I wish there was more I could say to try to diagnose the problem, but this is all I know. Is there any other information I could get you, or does anyone have any ideas why this is happening?

---

### Post by kirkio on 2006-10-12
nevermind, i figured it out.

---

### Post by ctrl_freak on 2006-10-18
And how did you fix it? I'm interested - I'm getting troubles running Steam and any suggestion to the solution might help...

Please post what you did! ;)

---

