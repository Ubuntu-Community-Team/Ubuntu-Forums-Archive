---
title: "Launcher points to the wrong folder?"
date: 2011-11-03
forum: Desktop Environments
---

### Post by Quaxo76 on 2011-11-03
I set up a launcher icon to run a Windows program I use a lot. I did it with unity-launcher-editor before upgrading from 11.04 to 11.10. But it has this problem: the file is run, but the "working folder" for the program is my home folder instead of the application's folder.

The application resides in /home/myname/path/to/app/ and creates and uses some config files; if I run it from Nautilus (or the terminal) it uses the config files in its own folder; while if I run it from the unity launcher, it creates and uses new config files in /home/myname/.
This of course doesn't work - I don't want to have two differing sets of settings. How can I tell the launcher to point to the right folder? I used a command like this: "wine /home/myname/path/to/app/application.exe"

Thanks,
Cristian

---

### Post by Quaxo76 on 2011-11-09
*Bump* Anyone?

---

### Post by mcduck on 2011-11-09
Create a simple script that moves you to correct location before launching the program, and then point the launcher to that script.

```
#! /bin/sh
cd /home/myname/path/to/app/
wine application.exe
```

(remember to make the script executable, of course)

edit: Actually, there's a better way. You should use "wine start" in the launcher to start programs with a path. It will automatically set the working directory:
```
wine start 'C:\path\to\application.exe'
```
or using Unix-style path:
```
wine start /Unix "$HOME/path/to/app/application.exe"
```

[http://wiki.winehq.org/FAQ#head-3b297df7a5411abe2b8d37fead01a2b8edc21619]("http://wiki.winehq.org/FAQ#head-3b297df7a5411abe2b8d37fead01a2b8edc21619")

---

### Post by Quaxo76 on 2011-11-09
> **mcduck said:**
> 
or using Unix-style path:
```
wine start /Unix "$HOME/path/to/app/application.exe"
```



That worked, thank you! It now opens a terminal before opening the application, but I can live with that.

Cristian

---

