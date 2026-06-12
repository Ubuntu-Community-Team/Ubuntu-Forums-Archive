---
title: "DosBox Config file location"
date: 2017-03-09
forum: Emulators
---

### Post by jobtmp on 2017-03-09
Hi,
Cannot find the DosBox config file. Tried to follow the instructions  from the DosBox chapter (see the copy below) but to no avail.

=======================================================
**Linux**

[COLOR=#000000][FONT=sans-serif]For Linux the configfile is created on the first run in ~/.dosbox/
The name is dosbox-*{version}*.conf where version is currently 0.74[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]On Ubuntu in the dosbox man file it is written:[/FONT][/COLOR]
 Configuration  and  language files use a format similar to Windows .ini
 files.  First ~/.dosboxrc (if present)  will be loaded. If  no  config&#8208;
 file  is  specified  at  the  commandline, a file named dosbox.conf (if
 present in the current directory) will be loaded  automatically  after&#8208;
 wards. If a configfile is specified at the commandline that one will be
 used instead.
=======================================================


Please advise. NB my initial  problem was switching to full-screen mode (Alt-Enter doesn't work) 
My current system is Ubuntu 16.10

---

### Post by Dennis N on 2017-03-09
The configuration file should be in a hidden folder (name starts with a . ) **[FONT=Courier New].dosbox[/FONT]** within your home folder. With the file manager, the view menu has an check option to show hidden files and folders, or use Ctrl+H to toggle visibility of hidden files and folders. 

In terminal:
```
dmn@Sydney:~$ ls .dosbox
backup  dosbox-0.74.conf  dosbox-0.74.conf.bak

```
The configuration file is dosbox-0.74.conf.

Running **dosbox** from the terminal should create a new folder and default configuration file if it is missing.

---

### Post by jobtmp on 2017-03-10
Merci beaucoup. Have found the file and changed **fullscreen** to* true*.  It worked as planned. The only remaining issue is that *Alt-Enter* which supposedly should toggle **fusscreen** still doesn't work. But I can live with that. Thanks a lot again.

---

### Post by oldrocker99 on 2017-03-10
Please mark this thread as [SOLVED] using the Thread Tools.

---

### Post by deadflowr on 2017-03-10
*Thread moved to **Emulators**.*

---

