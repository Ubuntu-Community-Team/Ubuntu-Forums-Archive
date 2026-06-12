---
title: "Way to find terminal name for applications"
date: 2012-10-07
forum: Desktop Environments
---

### Post by Azyx on 2012-10-07
Hi.
I old Ubuntu with gnome2 you could right-click the startup-link and choose preference and under Command you see the 'terminal name' for example:

'Log File Viewer' has the command 'gnome-system-log'

But now the you start an application in 12.04 Unity thru: Home-button and typing, the application appear very nice, but how do I find the name if I for instance need to run the application as super user?

/Cheers

---

### Post by 2F4U on 2012-10-07
Probably not the most elegant solution, but the folder /usr/share/applications has a lot of .desktop files, among them gnome-system-log.desktop. If you look into this file (it is a text file) you see

```
[Desktop Entry]
Name=Log File Viewer
Comment=View or monitor system log files
Exec=gnome-system-log
Icon=logview
Terminal=false
Type=Application
StartupNotify=true
Categories=GTK;GNOME;System;Monitor;
NotShowIn=KDE;
X-GNOME-DocPath=gnome-system-log/gnome-system-log.xml
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-utils
X-GNOME-Bugzilla-Component=logview
X-GNOME-Bugzilla-Version=3.4.1
X-Ubuntu-Gettext-Domain=gnome-system-log

```

The screen name is Log File Viewer and application name gnome-system-log is executed. So the name that appears behind exec is the command that gets executed.

---

### Post by hakermania on 2012-10-07
2F4U is correct, that is the best way (to look at the **Exec** field of the corresponding desktop file from /usr/share/applications)

Alternatively, you can open the System Monitor while the application is running so as to relieve its name. Note that by doing this there is a (very) rare case not to be able to launch the application through terminal just by typing its name you saw at the System Monitor, simply because it is not in $PATH.

---

### Post by vasa1 on 2012-10-07
So I guess some competent person could write a script to go through all the .desktop files and pull out just the relevant lines:```
[Desktop Entry]
Name=Log File Viewer
Comment=View or monitor system log files
Exec=gnome-system-log

```
to give something like:
```

Name=Log File Viewer --- Exec=gnome-system-log
Name=... --- Exec=...
Name=... --- Exec=...


```

---

### Post by MG&amp;TL on 2012-10-07
```
for files in /usr/share/applications/*.desktop; do grep -e "^Exec=" -e "^Name=" $files | sed 's/Exec=/Command: /g' | sed 's/Name=/Name: /g' && echo "-------------------------------"  ; done

```

seems to work okay. Returns list of commands and programs, separated by program.

Hope that helps.

---

### Post by vasa1 on 2012-10-07
> **MG&TL said:**
> ...
Hope that helps.
I could have done that ;)
Would have taken me a few weeks though.

Anyway, I modified it a bit to get the output as a file:
```
for files in /usr/share/applications/*.desktop; do grep -e "^Exec=" -e "^Name=" $files | sed 's/Exec=/Command: /g' | sed 's/Name=/Name: /g' >> mgtl.txt ; done

```

---

### Post by Azyx on 2012-10-07
You are great :) Thanks a lot every one :)

Cheers :)

---

### Post by vasa1 on 2013-01-25
@MG&TL, small problem ... some .desktop files have *Exec* **before** *Name*. LibreOffice components have this order :(

Actually, it's worse: they have Exec, Name and then a little lower down in the same .desktop file, there's Name, Exec. !!!

It's not a big deal but is there a way to ensure that the **output** is always in *Name*, *Command* order whether or not the .desktop has *Name* first and more than one Name= and Exec=?

---

