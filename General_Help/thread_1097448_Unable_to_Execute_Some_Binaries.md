---
title: "Unable to Execute Some Binaries"
date: 2009-03-16
forum: General Help
---

### Post by themusicdan on 2009-03-16
I switched from XP to Kubuntu/Ubuntu about 3-4 months ago, and everything has been pretty smooth. Unfortunately, yesterday I started having a problem opening binaries. I was trying to run yamipod to get some playlists off an ipod that I lost, and though I have followed all the instructions, when I open the binary that should start the program, it doesn't do anything. I decided to try with another program, so I went with floola, and again, nothing happened. I have been slowly coming to understand the way linux works, but I don't know where to look to see what types of errors the program might have encountered or what might have happened. Any help would be most appreciated. Thanks.

---

### Post by GeoMoon5 on 2009-03-16
I ran into the same problem when I was running 64 bit Ubuntu 8.10 server edition, and was unwittingly trying to execute a 32 bit binary. I wasn't able to get it to work until I apt-got the 32 bit libraries so the 64 bit OS could understand the 32 bit binary. Until I did that, every time I tried to execute the .bin, it just did nothing like you said.


Update: Oh it looks like you're running the desktop version of Ubuntu, I think the 64 bit version of that can handle 32 bit stuff, yes? So I guess what I said earlier isn't pertinent.

---

### Post by themusicdan on 2009-03-16
Yeah, I'm running the desktop version, and 32 bit at that, so it's not a 64 bit compatibility issue. Thanks, though.

---

### Post by cariboo on 2009-03-16
Try running the binary in a terminal and note any error messages.

Jim

---

### Post by orethrius on 2009-03-16
Those look like standalone apps, have you tried this?

1.  Right-click the program you want to run.
2.  Select "Properties".
3.  A dialog will open, click the "Permissions" tab.
4.  Towards the bottom, ensure that "Allow executing file as program" has a tick in the checkbox next to it.
5.  Click "Close" and try again.

If that doesn't do it, there are some other things to try, but I'd take the obvious approach first before getting into more detailed troubleshooting.  ;)

---

### Post by themusicdan on 2009-03-16
@cariboo907: I don't know if I'm doing this right, but navigating to the folder that contains the files and typing their names gives the following error: 

```
bash: YamiPod: command not found
```

It does the same for Floola, and before you ask, I did make sure that my capitalization was correct and that I spelled it right and everything else. I don't know what the command to open them in terminal is other than the name, though.

@orethrius: Yes, I have permission to execute them. That was already checked, so I did not change anything.

---

### Post by orethrius on 2009-03-16
Try this one:
```
./YamiPod
```

Using a command name by itself assumes that the application is installed in /usr/bin, which isn't always the case.  "./" in a Terminal indicates the current directory.

If the application can't be executed from its own directory via ./<appname>, then something more serious is at play here.

If this IS the problem, then - assuming the application is completely standalone - you can remedy it by doing this (hold Alt and hit F2 for a Run prompt):
```
gksudo nautilus /home& gksudo nautilus /usr/bin/&
```

Then, just open your home directory in the /home window, track down the proper executable, and drag-and-drop it to the /usr/bin window.

---

### Post by themusicdan on 2009-03-17
I got it to work! Thanks, orethrius! So using the ./YamiPod command, I found out that I lacked one of the program's dependencies. Apparently, both programs relied on me having a C++ package installed. Once I took care of that, it worked perfectly. Thanks for explaining the "./" structure. I really appreciate it.

---

