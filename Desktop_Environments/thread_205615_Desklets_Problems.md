---
title: "Desklets Problems"
date: 2006-06-28
forum: Desktop Environments
---

### Post by Sam Lars on 2006-06-28
Hello, a while ago I had gdesklets installed and I was very impressed.  Back in Janurary-Februrary they worked great... but something happened after that, and since then it has not started.  Typing "gdesklets" produces:

```
Starting gdesklets-daemon...
Connecting to daemon [    ###      ]You need a recent version of PyGTK to run this program.

Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.
```

The logfile has some stuff from back in March when the desklets worked, like error messages from the weather applet in retrieving the data.
And, of course, "pygtk" is not a package, and I have python2.4-gtk2, python-gtk-1.2, and python-gtk2 installed, so I don't know what it's looking for.
I have tried reinstalling gdesklets and gdesklets-data, which does nothing.  I even tried installing adesklets, but when I type "adesklets" into the terminal it just produces a new prompt and does nothing.
I've always been able to resolve my problems on my own, but this one's gone on long enough.  Any help is greatly appreciated!

---

### Post by taurus on 2006-06-28
Are you using an old version of pygtk?  See if you can upgrade it to a latest version and run gdesklets again...   Otherwise, remove gdesklets and install it again!  Gdesklets is running fine on my Dapper.

---

### Post by Sam Lars on 2006-06-28
As I said, I can't find pygtk, but I've got everything close to it installed, and Ubuntu seems to think that they're up to date.

---

### Post by taurus on 2006-06-28
I would use synaptic and remove the python-gtk-1.2 since you already have python-gtk2.

---

### Post by Sam Lars on 2006-06-28
Ok... I did as you said, removed that package with Synaptic, it took two of its friends with it (pythons gdk-imlib-1.2 and gnome-1.2)...
Gdesklets gives me the same thing and adesklets hasn't changed.

---

### Post by Sam Lars on 2006-06-28
Ok, still not working, and this is what "gdesklets check" spits out:

```
Checking requirements:
 - sys ... found
 - xml.parsers.expat ... found
 - xml.sax ... found
 - gtk ... missing
Version check failed.

GTK python bindings (pygtk2) version >= 2.4.0 and GTK+ version >= 2.4.0 are required.
```

Of course, I can't find anything related to the name "pygtk2," even less so than with "pygtk"...
I have python-gtk2 installed, which has to be what it's looking for...
So... I guess it doesn't work anyway, so I uninstalled python-gtk2 and all of the packages that depend on it (gdesklets one of them), then reinstalled it all.  Looked like this if you're interested:

 ```
sudo apt-get remove python-gtk2 && sudo apt-get install python-gtk2 deskbar-applet gdeskcal gdesklets gdesklets-data gimp-python gnome-app-install gnome-btdownload listen python-gst python-gst0.10 python-gtk2 pythoncad
```

And I'm left with the same problem.  Found this on another thread:

```
apt-get install python2.4-gtk2 python-gtk2 python-glade2 python2.4-glade2
```

And they're already installed.  So I guess I'll edit /usr/bin/gdesklets to ignore that (I think I've done this before...).  Which reminds me, am I supposed to get errors from gedit in the terminal?  This looks kind of familiar:

```

** (gedit:7217): WARNING **: Could not import pygtk
Traceback (most recent call last):
  File "/usr/lib/gedit-2/plugins/modelines.py", line 20, in ?
    import gedit
```

So I just commented out the little pygtk requirement check... yeah, that gives me a programming error.  I guess I don't know python well enough to know what to edit out. :( 
And back to the same error as before.  Any ideas?

---

### Post by Sam Lars on 2006-06-29
Ok, still nothing... I tried removing the different versions, like the lower ones, but, surprise, gdesklets depends on them.

---

