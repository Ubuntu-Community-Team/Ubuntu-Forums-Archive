---
title: "XFCE 4.8 and DockBarX"
date: 2011-04-12
forum: Desktop Environments
---

### Post by BrokenKingpin on 2011-04-12
I have install Xubuntu 11.04 and I am trying to add DockBarX to the panel, but it is not working.

I have installed the XfApplet, but when I try to add DockBarX to that it crashes.

I have installed DockBarX with these instructions.
[http://www.webupd8.org/2011/02/dockbarx-applet-043-released-with.html](http://www.webupd8.org/2011/02/dockbarx-applet-043-released-with.html)

Has anyone got this working successfully?

---

### Post by Copper Bezel on 2011-04-12
Is the problem related to one of [_these_]("http://ubuntuforums.org/showpost.php?p=9257575&postcount=3")?

I'm not seeing any success stories online about this process, but let's first check that you can run DockBarX at all, panel or no panel (as explained in the thread.)

---

### Post by M7S on 2011-04-13
Post your log (~/.dockbarx/log/dockbarx.log).

If you have no log, try running DockbarX in window and see if there's an error.
```
dockbarx_factory run-in-window
```

---

### Post by BrokenKingpin on 2011-04-13
When I run that command I get the following:
> 
$ dockbarx_factory run-in-window
Traceback (most recent call last):
  File "/usr/bin/dockbarx_factory", line 30, in <module>
    import gnomeapplet
ImportError: No module named bonobo.ui

I see the same thing in the log file.

---

### Post by BrokenKingpin on 2011-04-13
OK I got it working! I just had to install the python-gnome2 package. I will file a bug with DockBarX to ensure this is a dependency of the package. Thanks for the help. Sorry for the double post.

---

