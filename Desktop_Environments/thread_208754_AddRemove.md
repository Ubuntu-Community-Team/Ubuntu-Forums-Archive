---
title: "Add/Remove"
date: 2006-07-04
forum: Desktop Environments
---

### Post by thepocketdrummer on 2006-07-04
I try to open the Add / Remove Applications program and it checks for installed and available applications, then immediately closes. How do I fix this?

---

### Post by aysiu on 2006-07-04
Can you post the output of this terminal command? ```
gksudo gnome-app-install
```

---

### Post by thepocketdrummer on 2006-07-04
```
pocketdrummer@RyanGodBox:~$ gksudo gnome-app-install
warning: could not initiate dbus
** (gnome-app-install:5302): WARNING **: return value of custom widget handler was not a GtkWidget
Got non-package menu entry gnome-commander.desktop
Got non-package menu entry kiso.desktop
Got non-package menu entry k3dsurf.desktop
Got non-package menu entry xchm.desktop
Got non-package menu entry grdesktop.desktop
Got non-package menu entry tsclient.desktop
Got non-package menu entry granule.desktop
Got non-package menu entry kmyfirewall.desktop

(gnome-app-install:5302): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:5302): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:5302): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 40, in ?
    app = AppInstall(datadir, desktopdir, sys.argv)
  File "/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py", line 200, in __init__
    time_source = os.stat("/etc/apt/sources.list")[stat.ST_MTIME]
OSError: [Errno 2] No such file or directory: '/etc/apt/sources.list'
pocketdrummer@RyanGodBox:~$

```

---

### Post by aysiu on 2006-07-04
[This](http://ubuntuforums.org/showthread.php?t=184657) may help.

---

### Post by thepocketdrummer on 2006-07-05
umm... I have no clue what I'm supposed to do at this point. Is there any way you could sum up the steps I need to take?

I'm considering just reformatting (which is my linux problem solver at the moment.)

---

### Post by aysiu on 2006-07-05
Well, are you using Mozilla's Firefox (as opposed to Ubuntu's Firefox)?

---

### Post by thepocketdrummer on 2006-07-05
I'm using the one that came with Dapper Drake.

---

### Post by catellus on 2006-07-09
theposketdrummer wrote:
[INDENT]...Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 40, in ?
    app = AppInstall(datadir, desktopdir, sys.argv)
  File "/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py", line 200, in __init__
    time_source = os.stat("/etc/apt/sources.list")[stat.ST_MTIME]
OSError: [Errno 2] No such file or directory: '/etc/apt/sources.list'
pocketdrummer@RyanGodBox:~$[/INDENT]

Drummer,  note the next to last line.  You're missing the list of sources for applications (/etc/apt/sources.list).  Perhaps you modified the file and changed the name by  mistake.

---

