---
title: "Gnome shell not running in karmic"
date: 2010-03-04
forum: Desktop Environments
---

### Post by nirpius on 2010-03-04
I was trying to install gnome shell and run it on karmic and this has happened:

```

nirpius@ASPIREONE:~$ sudo apt-get build-dep gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

nirpius@ASPIREONE:~$ sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-shell is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

nirpius@ASPIREONE:~$ gnome-shell --replace
Failed to start shell
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
Cannot register the panel shell: there is already one running.
Traceback (most recent call last):
  File "/usr/bin/gnome-shell", line 265, in <module>
    shell = start_shell()
  File "/usr/bin/gnome-shell", line 138, in start_shell
    (server_glx_extensions, client_glx_extensions, glx_extensions) = _get_glx_extensions()
  File "/usr/bin/gnome-shell", line 67, in _get_glx_extensions
    glxinfo = subprocess.Popen(["glxinfo"], stdout=subprocess.PIPE)
  File "/usr/lib/python2.6/subprocess.py", line 621, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1126, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

```

So I looked on here and found this thread:

[http://ubuntuforums.org/showthread.php?t=1354787&highlight=gobject&page=2](http://ubuntuforums.org/showthread.php?t=1354787&highlight=gobject&page=2)

and following its advice I went here:

[http://packages.ubuntu.com/karmic/gnome-shell](http://packages.ubuntu.com/karmic/gnome-shell)

And installed everything manually thus:

```

nirpius@ASPIREONE:~$ sudo apt-get install gconf2 gjs gobject-introspection-freedesktop gobject-introspection-glib-2.0 gobject-introspection-repository libatk1.0-0 libc6 libcairo2 libclutter-1.0-0 libcroco3 libdbus-1-3 libdbus-glib-1-2 libfontconfig1 libfreetype6 libgconf2-4 libgirepository1.0-0 libgl1-mesa-glx libglib2.0-0 libgnome-desktop-2-11 libgnome-menu2 libgstreamer0.10-0 libgtk2.0-0 libnspr4-0d libpango1.0-0 librsvg2-2 libstartup-notification0 libx11-6 libxcomposite1 libxdamage1 libxext6 libxfixes3 libxml2 mutter zlib1g xserver-xephyr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gconf2 is already the newest version.
gjs is already the newest version.
gobject-introspection-freedesktop is already the newest version.
gobject-introspection-glib-2.0 is already the newest version.
gobject-introspection-repository is already the newest version.
libatk1.0-0 is already the newest version.
libc6 is already the newest version.
libcairo2 is already the newest version.
libclutter-1.0-0 is already the newest version.
libcroco3 is already the newest version.
libdbus-1-3 is already the newest version.
libdbus-glib-1-2 is already the newest version.
libfontconfig1 is already the newest version.
libfreetype6 is already the newest version.
libgconf2-4 is already the newest version.
libgirepository1.0-0 is already the newest version.
libgl1-mesa-glx is already the newest version.
libglib2.0-0 is already the newest version.
libgnome-desktop-2-11 is already the newest version.
libgnome-menu2 is already the newest version.
libgstreamer0.10-0 is already the newest version.
libgtk2.0-0 is already the newest version.
libnspr4-0d is already the newest version.
libpango1.0-0 is already the newest version.
librsvg2-2 is already the newest version.
libstartup-notification0 is already the newest version.
libx11-6 is already the newest version.
libxcomposite1 is already the newest version.
libxcomposite1 set to manually installed.
libxdamage1 is already the newest version.
libxdamage1 set to manually installed.
libxext6 is already the newest version.
libxfixes3 is already the newest version.
libxfixes3 set to manually installed.
libxml2 is already the newest version.
mutter is already the newest version.
mutter set to manually installed.
zlib1g is already the newest version.
xserver-xephyr is already the newest version.
xserver-xephyr set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

And lo and behold, when I do this:

```

nirpius@ASPIREONE:~$ gnome-shell --replace

```

I get this:

```

Failed to start shell
Traceback (most recent call last):
  File "/usr/bin/gnome-shell", line 265, in <module>
    shell = start_shell()
  File "/usr/bin/gnome-shell", line 138, in start_shell
    (server_glx_extensions, client_glx_extensions, glx_extensions) = _get_glx_extensions()
  File "/usr/bin/gnome-shell", line 67, in _get_glx_extensions
    glxinfo = subprocess.Popen(["glxinfo"], stdout=subprocess.PIPE)
  File "/usr/lib/python2.6/subprocess.py", line 621, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1126, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
Cannot register the panel shell: there is already one running.

```

---

### Post by fanum on 2010-03-09
Are you using the gnome-shell package supplied from ubuntu, or the PPA?

---

