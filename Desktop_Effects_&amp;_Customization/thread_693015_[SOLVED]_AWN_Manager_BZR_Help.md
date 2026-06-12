---
title: "[SOLVED] AWN Manager BZR Help"
date: 2008-02-10
forum: Desktop Effects &amp; Customization
---

### Post by vahnx on 2008-02-10
I found a way to fix this one problem I'm having with AWN, but at a cost. Here is a list of applets that appear as a white line and are unusable:
[i]Battery Applet
BlingSwitcher
Quit-Logoff applet
Media Icons Play
GMail Applet
Showdesktop Applet
Python Test Applet
Media Icons Back	
Clock (no white line, just dissapears)
Notification Area
Volume Control
Media Icons Next
Weather Applet
Media Control[/i]

They all look like this when added to the doc (look at the line standing on the right, the stuff behind is just my web browser):
[IMG]http://img85.imageshack.us/img85/4676/docwr8.jpg[/IMG]

And when an applet is added here is the output:
```
/home/drew/.gtkrc-2.0:2: error: scanner: unterminated string constant - e.g. `style'
APPLET : /usr/lib/awn/applets/showdesktop.desktop
Traceback (most recent call last):
  File "/usr/lib/awn/applets/showdesktop/showdesktop.py", line 38, in <module>
    import awn
ImportError: No module named awn

```

To fix it, you have to install awn-core-applets-bzr (which gives an error during install). Then it looks like normal:
[IMG]http://img216.imageshack.us/img216/7/doc2wu1.jpg[/IMG]

But by installing awn-core-applets-bzr, it breaks basically all update/install abilities of Ubuntu (such as Synaptics, Update Manager, and sudo apt-get) and you get this error saying E:/ python-libawn-bzr is broken, and I cannot fix it with a repair on broken packages by the command line or Synaptics. 

Here is the error when I go to install python-libawn-bzr, and when it's installed in this error state, the update manager icon appears in the system tray:
```
E: /var/cache/apt/archives/libawn-bzr_0.2.0-bzr155-1_i386.deb: trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn0
```

I believe people in [this]("http://ubuntuforums.org/showthread.php?p=4304000") thread are also having similar problems.

---

### Post by vahnx on 2008-02-12
OK I fixed this. I completely removed AWN Manager and all associated links. Then I just installed the stuff with AWN bzr and lib0 bzr and the applets work. For some reason though, it kept my configuration even tho I completely removed AWN. So anyone else having this trouble can now search and fix it.

---

