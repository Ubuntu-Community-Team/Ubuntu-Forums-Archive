---
title: "Issues with software-center and update-manager noticed after new setup"
date: 2015-02-19
forum: Desktop Environments
---

### Post by DCO on 2015-02-19
I apologize for giving 'my life story' so to speak, but I'm trying to make sure I give as much relevant information as possible.

Due to some stupid choices and laziness in backing up caused me to lose most of my recent files. I decided to just start clean trying Gnome this time instead of KDE. After installation, I set up many of my programs including putting some work into adding IdleX to the 'opens with' menu, and installing gnome 3.14 and fixing the problems with tweak tool start-programs tweak I was just about to try to re-install the Caffeine since after the gnome upgrade, the indicator toggle didn't appear to be working, when I try to open software-center and it hung. 

First, I ran it in terminal and got this:

```
(software-center:8619): Gtk-WARNING **: Theme file for default has no name


(software-center:8619): Gtk-WARNING **: Theme file for default has no directories

2015-02-19 13:30:56,294 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 607, in msg_reply_handler
    *message.get_args_list()))
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 69, in error_cb
    callback('')
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 169, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
```

I first set my tweaks back to adwaita to ensure there wasn't some problem I didn't understand, but that only got rid of the Gtk warnings. Realizing I could ignore that, I searched and tried different fixes found here and AskUbuntu forums. I tried several options from different posts, including:

purging and reinstalling software-center (including .config)
reinstalling adwaita-theme-full (just in case there was a call to a .css or something in default that needed a return)
reinstalling aptdaemon
installing App Grid (to see if it was only a Python 2.7 issue - it's not) - App grid starts, but has the same issue as software-center when trying to install or remove

Then I found this old thread:
[http://ubuntuforums.org/showthread.php?t=2120301](http://ubuntuforums.org/showthread.php?t=2120301)

My outputs were mostly the same, (with higher version numbers,) including no putput from dpkg -C. That is up until the suggested command:

```
sudo start-stop-daemon -S --exec /usr/sbin/aptd -- -d
```

This produced the results:

```
12:13:04 AptDaemon [INFO]: Initializing daemon
12:13:04 AptDaemon.Worker [DEBUG]: using high-trust whitelist: 'set()'
Traceback (most recent call last):
  File "/usr/sbin/aptd", line 39, in <module>
    aptdaemon.core.main()
  File "/usr/lib/python3/dist-packages/aptdaemon/core.py", line 2180, in main
    daemon = AptDaemon(options, bus=bus)
  File "/usr/lib/python3/dist-packages/aptdaemon/core.py", line 1452, in __init__
    load_plugins)
  File "/usr/lib/python3/dist-packages/aptdaemon/worker/pkworker.py", line 164, in __init__
    aptworker.AptWorker.__init__(self, chroot, load_plugins)
  File "/usr/lib/python3/dist-packages/aptdaemon/worker/aptworker.py", line 204, in __init__
    "get_license_key"])
  File "/usr/lib/python3/dist-packages/aptdaemon/worker/__init__.py", line 191, in _load_plugins
    dists, errors = pkg_resources.working_set.find_plugins(env)
  File "/usr/local/lib/python3.4/dist-packages/setuptools-12.2-py3.4.egg/pkg_resources/__init__.py", line 871, in find_plugins
  File "/usr/local/lib/python3.4/dist-packages/setuptools-12.2-py3.4.egg/pkg_resources/__init__.py", line 977, in __init__
  File "/usr/local/lib/python3.4/dist-packages/setuptools-12.2-py3.4.egg/pkg_resources/__init__.py", line 1007, in scan
  File "/usr/local/lib/python3.4/dist-packages/setuptools-12.2-py3.4.egg/pkg_resources/__init__.py", line 1027, in add
TypeError: unorderable types: NoneType() < str()
```

Noticing that is the same type of problem, I tried to view the article suggested as the answer, namely:
[http://www.usr-local-share.com/?p=594](http://www.usr-local-share.com/?p=594)

However, it seems this site no longer exists. Rather than necroing that old post, I'm posting here, hoping someone can pick up where that other thread leaves off.

---

### Post by DCO on 2015-02-20
I was trying to show the steps and research I have already done in hopes of a faster reply (that was something other than STFW or something like that). I was going to try to include the crash report I got this morning because I lapsed and tried to let the update notifier install the updates.  However, that's too big and nearly froze my system indicating how much information is in the gedit version. 

I'm not a Linux expert by any means, only good at searching. So I could really use help with this matter, as since that site apparently doesn't exist anymore, I'm not sure where else to go to learn more about this problem. 

In the meantime, I guess it's back to researching in order to figure out how to manually install the security updates that were offered today.

---

### Post by ian-weisser on 2015-02-21
I would try reinstalling aptdaemon.

---

### Post by DCO on 2015-02-21
Thanks for the reply. 

That was one of the first things I tried, but there was apparently a setting or something that kept reinstalling with it. Which was part of why I was asking for help. While I was still waiting for a response last night I started following the setuptools error.

I found that pip and setuptools were influencing apt-worker in python3 creating a None type where it expected a string in pkg_resources.py,  I found this by deleting setuptools as suggested in [https://pypi.python.org/pypi/setuptools/0.9.8#installation-instructions](https://pypi.python.org/pypi/setuptools/0.9.8#installation-instructions) under the uninstall heading. Upon deleting pkg_resources.py, I found it was an import in python3's apt-worker. 

However, at this point, it was getting late and I was getting tired so decided to try "one more thing" before calling it a night. I was going to purge and re-install python3.

Pro-tip: don't do this when you're really tired!!!! After purging it automatically runs apt-get autoremove. Being as tired as I was, I didn't think and typed y.

So while I'm re-building my system. I'll install Idlex last to make sure that was the only issue causing that before I mark as solved.

---

### Post by DCO on 2015-02-21
Well I have everything re-installed (except setuptools and Idlex) and everything is almost back to how it was. It appears that was it after all I guess I'll look for a better alternative.

---

