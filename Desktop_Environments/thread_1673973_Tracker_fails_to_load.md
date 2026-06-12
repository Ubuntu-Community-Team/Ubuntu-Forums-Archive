---
title: "Tracker fails to load"
date: 2011-01-23
forum: Desktop Environments
---

### Post by Jim_Hope on 2011-01-23
Whenever I boot up (X61 running Ubuntu 10.10), the tracker fails to load. In .xsessions, I get the following error:

Tracker-Message: Setting up monitor for changes to config file:'/home/lacfadio/.config/tracker/tracker-status-icon.cfg'

(polkit-gnome-authentication-agent-1:2847): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:2847): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
17
Failure: Module initalisation failed
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
  set_interactive(1)
Tracker-Message: Loading defaults into GKeyFile...
Tracker-Message: Log verbosity is set to 0, disabling D-Bus client lookup
** Message: Loading defaults into GKeyFile...

** (tracker-status-icon:2828): WARNING **: Binding '<Ctrl><Alt>S' failed!

Tracker-Message: Registering D-Bus service...
  Name:'org.freedesktop.Tracker1'
Tracker-Message: Loading defaults into GKeyFile...
Starting log:
  File:'/home/lacfadio/.local/share/tracker/tracker-store.log'
Starting log:
  File:'/home/lacfadio/.local/share/tracker/tracker-miner-fs.log'

(Do:2826): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

I have searched the forums, but cannot find much on this that I can understand. Does anyone have a sense of what the error is, and how I might solve it?

cheers,

Jim.

---

### Post by AlwaysLearning on 2011-02-01
Have you tried using Synaptic to reinstall: tracker-gui, libgtk2.0-0 and python-gtkglext1?

If tracker's config files are broken you might also have some success dumping its config and catalog files:
```
tracker-config -r
tracker-config -s
tracker-status-icon
```

Good luck,
AL.

---

### Post by Jim_Hope on 2011-02-01
Dear AL,

Thanks for all your suggestions. 

I reinstalled tracker-gui, libgtk2.0-0 and python-gtkglext1 as suggested. However, the tracker still seems to have problems. The desktop still takes a long time to load and when I open up .xsessionserrors I see the following tracker error repeatedly:

(tracker-miner-fs:2793): Tracker-CRITICAL **: Could not execute sparql: Unable to insert multiple values for subject `urn:software-category:%2Fusr%2Fshare%2Fdesktop-directories%2Fkde-internet-terminal.directory' and single valued property `nfo:fileLastModified' (old_value: '<untransformable>', new value: '<untransformable>')

When I try to dump the config and catalog files, and use tracker-config -r, I receive the following message:

tracker-config: command not found

I have looked for tracker-config in the package manager, but it is not listed -- any ideas?

best,

Jim.

---

### Post by Backharlow on 2011-02-13
A couple things:

tracker-config is actually tracker-control

I got that as well, when i tried to start tracker while it was already running.
```
(tracker-miner-fs:2793): Tracker-CRITICAL **: Could not execute sparql: Unable to insert multiple values for subject `urn:software-category:%2Fusr%2Fshare%2Fdesktop-directories%2Fkde-internet-terminal.directory' and single valued property `nfo:fileLastModified' (old_value: '<untransformable>', new value: '<untransformable>')

```


remove old store:
```

tracker-control -r
```

Then log out and back in, and it will start up automatically and begin a new store.

or instead of getting new Gnome session you can just restart tracker with:
```
tracker-control -s
tracker-status-icon
```
but i think there might be some other magic going on when it gets a new gnome session, so try that.

---

### Post by Jim_Hope on 2011-02-14
Backharlow,

Great thanks, that seemed to solve it -- the error no longer comes up in x.sessions (though there are hundreds of other errors, sigh). I'll mark the thread solved. 

cheers,

Jim.

---

