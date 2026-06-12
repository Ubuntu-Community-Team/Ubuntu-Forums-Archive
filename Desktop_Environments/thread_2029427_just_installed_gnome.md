---
title: "just installed gnome"
date: 2012-07-19
forum: Desktop Environments
---

### Post by godfreezone on 2012-07-19
could someone kindly interpret the following output for me:
i enter
gnome-tweak-tool
and get
```
godfree@greg:~$ gnome-tweak-tool
WARNING : Error detecting shell
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell_extensions.py", line 149, in __init__
    shell = GnomeShellFactory().get_shell()
  File "/usr/lib/python2.7/dist-packages/gtweak/utils.py", line 38, in getinstance
    instances[cls] = cls()
  File "/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py", line 143, in __init__
    proxy = _ShellProxy()
  File "/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py", line 44, in __init__
    result, output = self.proxy.Eval('(s)', js)
  File "/usr/lib/python2.7/dist-packages/gi/overrides/Gio.py", line 148, in __call__
    kwargs.get('flags', 0), kwargs.get('timeout', -1), None)
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 43, in function
    return info.invoke(*args, **kwargs)
GError: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.Shell was not provided by any .service files
WARNING : Shell not running
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell.py", line 58, in __init__
    self._shell = GnomeShellFactory().get_shell()
  File "/usr/lib/python2.7/dist-packages/gtweak/utils.py", line 38, in getinstance
    instances[cls] = cls()
  File "/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py", line 143, in __init__
    proxy = _ShellProxy()
  File "/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py", line 44, in __init__
    result, output = self.proxy.Eval('(s)', js)
  File "/usr/lib/python2.7/dist-packages/gi/overrides/Gio.py", line 148, in __call__
    kwargs.get('flags', 0), kwargs.get('timeout', -1), None)
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 43, in function
    return info.invoke(*args, **kwargs)
GError: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.Shell was not provided by any .service files
WARNING : Could not list shell extensions
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell.py", line 63, in __init__
    extensions = self._shell.list_extensions()
AttributeError: ShellThemeTweak instance has no attribute '_shell'

(gnome-tweak-tool:2754): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2754): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2754): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2754): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2754): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2754): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2754): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2754): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2754): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2754): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2754): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2754): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2754): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2754): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2754): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2754): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 25

(gnome-tweak-tool:2754): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 25

(gnome-tweak-tool:2754): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 25

(gnome-tweak-tool:2754): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 25

(gnome-tweak-tool:2754): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 25

(gnome-tweak-tool:2754): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 25

(gnome-tweak-tool:2754): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 25

(gnome-tweak-tool:2754): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 25

(gnome-tweak-tool:2754): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 25

(gnome-tweak-tool:2754): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 25

(gnome-tweak-tool:2754): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 25

(gnome-tweak-tool:2754): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 25

(gnome-tweak-tool:2754): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 25

(gnome-tweak-tool:2754): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 25

(gnome-tweak-tool:2754): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 25
godfree@greg:~$ 

```
generally, my system seems to run a bit slower, though I wonder if this is not a function of my getting used to (surprisingly big) difference in environment features

ancillary question: must i launch tweak tool from terminal or can i pin it in some way to my start-up like i could in ubuntu's default environment
thx for any help
Godfrey

---

### Post by markbl on 2012-07-19
Looks like a compatability issue of some type. I notice my gnome-tweak-tool version comes from the gnome 3 ppa. IMHO it is best to add the gnome 3 team ppa when using gnome shell on ubuntu.
```

sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
audo apt-get install gnome-shell gnome-tweak-tool

```
Then reboot and log in to GNOME (i.e. gnome-shell). Like Unity, the easiest and quickest way to start apps is to use the search. I.e. press the super key and then "tw<enter>" should be enough to find & start the gnome-tweak-tool. Most people seem to agree that gnome-shell demands less system resources than unity so should run better on older hardware.

---

### Post by Frogs Hair on 2012-07-19
In the Gnome Shell move the cursor to the top left corner select applications and choose the advanced settings icon. Once open you can right click the icon to add it to the favorites bar on the left. I don't know about the errors in the terminal though.

[https://live.gnome.org/GnomeShell/CheatSheet](https://live.gnome.org/GnomeShell/CheatSheet)

---

### Post by markbl on 2012-07-19
> **Frogs Hair said:**
> 
[https://live.gnome.org/GnomeShell/CheatSheet](https://live.gnome.org/GnomeShell/CheatSheet)
Good point. **Every** new gnome shell user should spend their first 5 mins going through this excellent short summary. It describes is everything you need to know about the gnome shell.

---

### Post by godfreezone on 2012-07-19
Thanks folks, tried the code fix: didn't have any effect
Will get the cheat and try to figure it out for myself: bout time i  learned how to fly this magic carpet anyway.

thx again,
Godfrey

ps: now my alt+tab switch is not working .....

---

### Post by markbl on 2012-07-19
"Code fix"? So you added that ppa? Are you sure all your packages are up to date after adding that and have you rebooted?
```

sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by godfreezone on 2012-07-19
> **markbl said:**
> "Code fix"? So you added that ppa? Are you sure all your packages are up to date after adding that and have you rebooted?
```

sudo apt-get update
sudo apt-get dist-upgrade

```


thanks for sticking with me on this one;
just acting on above now; will update you on it in a tick

---

### Post by godfreezone on 2012-07-19
After putting your kindly offered code into terminal, then rebooting, then trying 
same command again, i still get critical error message, but! and this is important!, 
the terminal doesn't hang (don't know technical word, but it doesn't keep vainly trying to run the command: it stops and giives me my $ prompt back again!!@! which is progress
i include the current output just in case it means sthg to you 

once again, Mark, thx kindly
Godfrey
PS after the -distro update command, my alt/tab is working normally again!!!!!:P

[```
CODEgodfree@greg:~$ gnome-tweak-tool

(gnome-tweak-tool:2916): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2916): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2916): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2916): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2916): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2916): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2916): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2916): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2916): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2916): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2916): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2916): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2916): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2916): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2916): Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

(gnome-tweak-tool:2916): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 31

(gnome-tweak-tool:2916): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 31

(gnome-tweak-tool:2916): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 31

(gnome-tweak-tool:2916): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 31

(gnome-tweak-tool:2916): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 31

(gnome-tweak-tool:2916): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 31

(gnome-tweak-tool:2916): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 31

(gnome-tweak-tool:2916): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 31

(gnome-tweak-tool:2916): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 31

(gnome-tweak-tool:2916): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 31

(gnome-tweak-tool:2916): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 31

(gnome-tweak-tool:2916): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 31

(gnome-tweak-tool:2916): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 31

(gnome-tweak-tool:2916): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 31

(gnome-tweak-tool:2916): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 31
godfree@greg:~$ 
```

---

### Post by markbl on 2012-07-19
Those GT-critical and warnings are normal. I see them too when I start tweak tool from a terminal. Normally you would start this tool from search as I say above, or by clicking on it so you would not see those. The app appears for me after printing those messages, are you saying the app does not appear on your screen after you start it? Press the super key - the app is not hiding under your terminal window is it?

---

### Post by godfreezone on 2012-07-19
> **markbl said:**
> Those GT-critical and warnings are normal. I see them too when I start tweak tool from a terminal. Normally you would start this tool from search as I say above, or by clicking on it so you would not see those. The app appears for me after printing those messages, are you saying the app does not appear on your screen after you start it? Press the super key - the app is not hiding under your terminal window is it?


Ah, many thousands of humble pardons; weak-minded, aged newbie failed to explain:
the tool works! i see it, I tweak it!

What was a concern, and no longer is a concern, thanks to you, was the critical error messsage and the fact that my interogation of the wild, as-yet-untamed terminal line was leading to its hanging up on me, which i stress! it no longer does...

problem solved; crouching tiger, well, crouching in corner till next time i grab my tiger taming tool and boldly stride forth to tame...

regs,
Godfrey

---

