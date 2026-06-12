---
title: "Cant update repository in software update or add/remove"
date: 2006-09-17
forum: Desktop Environments
---

### Post by cdeatherage on 2006-09-17
Hello,

I am a newbie and have searched aroud the forums and didnt seem to find an answer to the problem I am having, so I thought I would give this a shot.  Lately I have had problems while opening the add/remove software under applications and the window will not open and gives me the error:

Introspect error: The name org.freedesktop.AppInstall was not provided by any .service files
no listening object (The name org.freedesktop.AppInstall was not provided by any .service files)

** (gnome-app-install:16705): WARNING **: return value of custom widget handler was not a GtkWidget
Got non-package menu entry gnome-commander.desktop
Got non-package menu entry kiso.desktop
Got non-package menu entry k3dsurf.desktop
Got non-package menu entry xchm.desktop
Got non-package menu entry grdesktop.desktop
Got non-package menu entry tsclient.desktop
Got non-package menu entry granule.desktop
Got non-package menu entry kmyfirewall.desktop

(gnome-app-install:16705): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:16705): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:16705): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 40, in ?
    app = AppInstall(datadir, desktopdir, sys.argv)
  File "/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py", line 200, in __init__
    time_source = os.stat("/etc/apt/sources.list")[stat.ST_MTIME]
OSError: [Errno 2] No such file or directory: '/etc/apt/sources.list'

I am guessing that something happened to my sources.list?  I did install bumps, could this have caused the issue?

Thanks for the help.

---

### Post by croak77 on 2006-09-17
Do you have a /etc/apt/sources.list? Take a look. If there isn't one there then there might be a backup sources.list in the same directory.

---

### Post by cdeatherage on 2006-09-17
it doesnt looki like I have it there.  when I look at the directory, this is what I see. 

cdeatherage@cdeatherage-laptop:/etc/apt$ dir
apt.conf     sources.list.bumps.09.16.06  trustdb.gpg
apt.conf.d   sources.list.d               trusted.gpg
secring.gpg  sources.list.save            trusted.gpg~

any suggestions?

---

### Post by croak77 on 2006-09-18
Take a look at sources.list.bumps.09.16.06. That might be your old sources.list pre bumps. I'm not familier with bumps. Usually I advise not using tools like this. Here's a default sources.list with multiverse and universe enabled for dapper.

```

## All officially supported packages, including security- and other updates
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
 
## The source packages (only needed to recompile existing packages)
#deb-src http://archive.ubuntu.com/ubuntu dapper main restricted
#deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
#deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted
 
## All community supported packages, including security- and other updates
deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
 
## The source packages (only needed to recompile existing packages)
#deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse
#deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse

```

Then open a terminal and type;
```
 sudo aptitude update
```

If you are looking to install multimedia codecs/plugins, go here;

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

