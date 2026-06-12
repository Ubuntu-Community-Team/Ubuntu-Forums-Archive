---
title: "a very serious problem with compiz - please help"
date: 2009-01-01
forum: General Help
---

### Post by Riven213 on 2009-01-01
Hello

I've been tweaking my compiz seetings in the ccsm when something very odd happened. I enabled the enhanced zoom plugin (or maybe the other zoom plugin, I don't rermember now) and the moment I clicked, the display went off, some green lines appeared and I was instantly at the login screen. The same thing happens now each time I log on my account. I am now writing from a different login. Compiz looks and works great without  any problems here, so this must be the question of that option I turned on back there.

I logged in as the user of the damaged account through the terminal and wanted to change the settings via ccsm, however, it won't launch displaying:

```
No protocol specified
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 100, in <module>
    import ccm
  File "/usr/lib/python2.5/site-packages/ccm/__init__.py", line 1, in <module>
    from ccm.Conflicts import *
  File "/usr/lib/python2.5/site-packages/ccm/Conflicts.py", line 27, in <module>
    from ccm.Constants import *
  File "/usr/lib/python2.5/site-packages/ccm/Constants.py", line 38, in <module>
    CurrentScreenNum = gtk.gdk.display_get_default().get_default_screen().get_number()
AttributeError: 'NoneType' object has no attribute 'get_default_screen'

```

Neither can I launch ANY other application this way - it displays:

```
No protocol specified
Error: cannot open display: :0.0

```

This is particularly weird. I understand that something may be wrong with compiz, but why can't I run applications? If I login as root, they launch without problems. But obviously this does not help, because I want to change settings on the damaged account.

There is also another, even stranger thing: I cannot use the text terminal. When I try to launch any of the workspaces, some green lines appear appear on the screen and nothing happens. All I can do is come back to the graphical mode. 

Now what does this mean? I've only enabled a simple effect in Compiz and now I'm unable to login, use the text terminal or launch applications :(

I have an Intel x3000 graphic card, if that changes anything...

---

### Post by Forlong on 2009-01-02
You can not run a graphical application like ccsm in plain text mode.
The X server need to be running.

Here's how to fix this: [http://ubuntuforums.org/showthread.php?t=1001005&p=6305740](http://ubuntuforums.org/showthread.php?t=1001005&p=6305740)

---

