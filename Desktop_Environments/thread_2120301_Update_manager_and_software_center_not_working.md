---
title: "Update manager and software center not working"
date: 2013-02-26
forum: Desktop Environments
---

### Post by lalorca on 2013-02-26
Hello all,

I am beginning to use Ubuntu 12.02, and I have problems with the Update Manager and the software center (I guess something must be wrong with my repository list...).

The update Manager freezes when I click on install updates (and gives me lots of suggestions even though I regularly run apt-get upgrade and apt-get update), and the software center just won't start (it just shows a grey window).

I have been trying to uninstall them both from terminal, update and upgrade, and re-install them, but it did not change anything.

Any help would be welcome !

---

### Post by matt_symes on 2013-02-26
Hi

Need much more info to start with.

Start update-manager and software-center from the terminal and post the output back here.

```
update-manager
```

```
software-center
```

Also from the terminal post the output of

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

Post between code tags like this [noparse]```
text
```[/noparse] to get output like this
```
text
```

That should give a starting point to diagnose as opposed to offering random terminal commands :D

Kind regards

---

### Post by lalorca on 2013-02-26
Hi,

Thanks for helping.

a) For update-manager, nothing is printed out in the terminal, clicking on install update just does not do anything.

b) For software-center:

```

2013-02-26 13:17:32,869 - dbus.connection - ERROR - Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 230, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 65, in signal_cb
    callback(new_owner)
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 156, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2013-02-26 13:17:32,876 - softwarecenter.ui.gtk3.app - INFO - closing before the regular main loop was run

```


Hoping this can help to solve the problem,

Laureline

---

### Post by matt_symes on 2013-02-26
Hi

Please use code tags. I have edited your last post.

Kind regards

---

### Post by lalorca on 2013-02-26
Sorry for the code tags, I had indeed not been able to understand what this meant in your first post - I am just beginning to use these forums.

Concerning the problem, do you think this is solvable ?

Thanks anyway for your time.

---

### Post by matt_symes on 2013-02-26
Hi

> **lalorca said:**
> Sorry for the code tags, I had indeed not been able to understand what this meant in your first post - I am just beginning to use these forums.

Concerning the problem, do you think this is solvable ?

Thanks anyway for your time.

No problem. I was not trying to have a go. I was just trying to help you out in forum etiquette.

Code tags make code much easier to read. There is also quote tags for when you are quoting someone from a previous post.

```
DBusException: orgreedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
```

This is the problem and is why software-center is hanging. I suspect its the same problem with update manager as well.

dbus is used to send messages around the system. It's sent a message but not got a response and so is hanging. The problem may be elsewhere then and would explain why reinstalloing software-center and update-manager did not work.

It would need some research.

Kind regards

---

### Post by schragge on 2013-02-26
I suppose the command-line package management tools are working fine, still I'd like to see the output of
```

sudo dpkg -C

```just to be sure that there's no installed, but unconfigured packages on your system. 

Also, please post the output of
```

apt-cache policy software-center
dpkg -l policykit\*|grep -o '^i. *[^ ]* *[^ ]*'

```

---

### Post by lalorca on 2013-02-26
Thanks for helping.

a) Nothing is printed out when typing:
```

sudo dpkg -C

```

b) The output of 
```

apt-cache policy software-center

```

is

```

software-center:
  Installed: 5.2.7
  Candidate: 5.2.7
  Version table:
 *** 5.2.7 0
        500 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     5.2 0
        500 http://fr.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

c) The output of

```

dpkg -l policykit\*|grep -o '^i. *[^ ]* *[^ ]*'

```

is

```

ii  policykit-1                            0.104-1ubuntu1
ii  policykit-1-gnome                      0.105-1ubuntu3.1
ii  policykit-desktop-privileges           0.10

```

---

### Post by matt_symes on 2013-02-26
Hi

I am not using Ubuntu at the moment so i'm not using software-center so i may not be much help but there are some things to check.

Can you post the output of

```
ls -l /usr/share/polkit-1/actions/
```to see if there is a policy for software updates and if there is to check it.

I'm thinking something along the lines of org.debian.apt.policy. 

EDIT: If the messages that software-center and update-manager are sending can be found then dbus-send and dbus-monitor can be used to see what is happening as well.

Kind regards

---

### Post by lalorca on 2013-02-26
Dear Matt,

So, the output of:
```

ls -l /usr/share/polkit-1/actions/

```

is

```

-rw-r--r-- 1 root root    703 Jul 10  2012 com.hp.hplip.policy
-rw-r--r-- 1 root root   2020 Jan 26 01:24 com.ubuntu.devicedriver.policy
-rw-r--r-- 1 root root    790 Apr 18  2012 com.ubuntu.languageselector.policy
-rw-r--r-- 1 root root    740 Apr 17  2012 com.ubuntu.pkexec.synaptic.policy
-rw-r--r-- 1 root root    848 Sep 28 16:06 com.ubuntu.softwareproperties.policy
-rw-r--r-- 1 root root   2627 Jan 10  2012 com.ubuntu.systemservice.policy
-rw-r--r-- 1 root root   1930 Apr 16  2012 com.ubuntu.usbcreator.policy
-rw-r--r-- 1 root root    817 Dec 13 19:55 com.ubuntu.whoopsiepreferences.policy
-rw-r--r-- 1 root root   5573 Dec 12 15:15 org.debian.apt.policy
-rw-r--r-- 1 root root    787 Dec 31  2011 org.debian.aptxapianindex.policy
-rw-r--r-- 1 root root    821 Apr 16  2012 org.debian.pkexec.gnome-system-log.policy
-rw-r--r-- 1 root root  11897 Oct  5 00:51 org.freedesktop.accounts.policy
-rw-r--r-- 1 root root   7303 Oct 24 00:21 org.freedesktop.color.policy
-rw-r--r-- 1 root root   1652 Feb 25  2012 org.freedesktop.consolekit.policy
-rw-r--r-- 1 root root   2108 Jan 10  2012 org.freedesktop.hostname1.policy
-rw-r--r-- 1 root root   1488 Jan 10  2012 org.freedesktop.locale1.policy
-rw-r--r-- 1 root root   2609 Mar 24  2012 org.freedesktop.modem-manager.policy
-rw-r--r-- 1 root root 103475 Oct 17 00:46 org.freedesktop.NetworkManager.policy
-rw-r--r-- 1 root root   1524 May 17  2012 org.freedesktop.policykit.policy
-rw-r--r-- 1 root root   1489 Oct 24  2011 org.freedesktop.RealtimeKit1.policy
-rw-r--r-- 1 root root  19039 Jul 17  2012 org.freedesktop.udisks.policy
-rw-r--r-- 1 root root   2290 Apr 13  2012 org.freedesktop.upower.policy
-rw-r--r-- 1 root root   5133 Apr 13  2012 org.freedesktop.upower.qos.policy
-rw-r--r-- 1 root root    829 Jan 30 17:07 org.gnome.settingsdaemon.datetimemechanism.policy
-rw-r--r-- 1 root root    964 Jan 30 17:07 org.gnome.settings-daemon.plugins.power.policy
-rw-r--r-- 1 root root    987 Jan 30 17:07 org.gnome.settings-daemon.plugins.wacom.policy
-rw-r--r-- 1 root root  12950 Sep  8 05:55 org.kde.kcontrol.kcmremotewidgets.policy
-rw-r--r-- 1 root root   1178 Apr  1  2012 org.kubuntu.qaptworker.policy
-rw-r--r-- 1 root root   1070 Jan 13  2012 screenresolution-mechanism.policy

```

I join a copy of the file org.debian.apt.policy you were interested in.

---

### Post by schragge on 2013-02-26
The permissions look OK to me. Try to call aptdaemon from the command line
```

aptdcon -d --upgrade-system

```

---

### Post by matt_symes on 2013-02-26
Hi

The file itself looks alright to me as well. The only thing it may be missing is the
```

<action id="org.debian.apt.install-packages.high-trust-repo">
    
    <description gettext-domain="aptdaemon">Install software from a high-trust whitelisted repository.</description>
    <message gettext-domain="aptdaemon">To install software, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>
```

I'm looking at org.debian.apt from 12.10 though.

For just a sanity check, can you post the output of

```
ps aux | grep dbus
```

Kind regards

---

### Post by lalorca on 2013-02-26
So:

a) To schragge:

The output of

```

aptdcon -d --upgrade-system

```

is an error (and I have a window 'System program problem detected' opening; Compiz and aptdcon are closing unexpectedly, and I am informed that error report belong to a non-available package)

```

Traceback (most recent call last):n                                      
  File "/usr/lib/python2.7/dist-packages/defer/__init__.py", line 389, in _next
    self.result = callback(self.result, *args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/client.py", line 1595, in on_error
    error_handler(error)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/errors.py", line 181, in <lambda>
    lambda err: error_handler(get_native_exception(err))
  File "/usr/lib/python2.7/dist-packages/aptdaemon/console.py", line 382, in _on_exception
    sys.exit(msg)
SystemExit: ERROR: org.freedesktop.DBus.Error.NoReply - Message did not receive a reply (timeout by message bus)

```


b) To Matt:

The output of

```

ps aux | grep dbus

```

is

```

103        979  0.0  0.0  25212  2472 ?        Ss   12:22   0:02 dbus-daemon --system --fork --activation=upstart
1000      1875  0.0  0.0  12492   320 ?        Ss   12:23   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session --session=ubuntu
1000      1878  0.0  0.0  26556   796 ?        S    12:23   0:00 /usr/bin/dbus-launch --exit-with-session gnome-session --session=ubuntu
1000      1879  0.0  0.0  27960  3748 ?        Ss   12:23   0:05 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
root      5406  0.0  0.2 179688 19504 ?        S    12:33   0:00 python /usr/lib/software-properties/software-properties-dbus
1000      9207  0.0  0.0   9400   920 pts/0    S+   15:11   0:00 grep --color=auto dbus

```

Concerning your note about some lines of code missing in org.debian.apt.policy, would you recommend to add them ?


Thanks very much to both of you.

---

### Post by matt_symes on 2013-02-26
Hi

Aptdaemon is the problem then. 

Some sanity checking. Can you post the output of

```
apt-cache policy aptdaemon
``````
dpkg -l aptdaemon
```@[[COLOR=#000000]lalorca[/COLOR]]("http://ubuntuforums.org/member.php?u=1793503") Well see bout that extra text later.

Kind regards

---

### Post by lalorca on 2013-02-26
So, typing:
```

apt-cache policy aptdaemon

```

I get:
```

aptdaemon:
  Installed: 0.43+bzr805-0ubuntu7
  Candidate: 0.43+bzr805-0ubuntu7
  Version table:
 *** 0.43+bzr805-0ubuntu7 0
        500 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/main amd64 Packages
        100 /var/lib/dpkg/status
     0.43+bzr805-0ubuntu1 0
        500 http://fr.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages

```



And typing
```

dpkg -l aptdaemon

```

gives

```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  aptdaemon      0.43+bzr805-0u transaction based package management service

```

Thanks again !

---

### Post by schragge on 2013-02-26
Does sending messages over D-BUS manually work?
```

dbus-send --system --dest=org.debian.apt --type=signal /org/debian/apt org.debian.apt.CacheChanged

```

---

### Post by matt_symes on 2013-02-26
Hi

Can you post the output of

```
ls -l /etc/apt/apt.conf.d/20dbus
``````
cat /etc/apt/apt.conf.d/20dbus
```and finally

```
sudo start-stop-daemon -S --exec /usr/sbin/aptd -- -d
```EDIT: Post the output after it has been running for a couple of minutes please

EDIT2:

and the output of these commands

```
ls -l /etc/dbus-1/system.d/org.debian.apt.conf
```

```
cat /etc/dbus-1/system.d/org.debian.apt.conf
```

Kind regards

---

### Post by lalorca on 2013-02-26
a) To schragge:

```

dbus-send --system --dest=org.debian.apt --type=signal /org/debian/apt org.debian.apt.CacheChanged

```

Gives an error in a window (System program error detected, 'Ubuntu has experienced an internal error') ; and nothing in the terminal.

b) To Matt:

1)
```

ls -l /etc/apt/apt.conf.d/20dbus

```

gives

```

-rw-r--r-- 1 root root 243 Dec 16  2009 /etc/apt/apt.conf.d/20dbus

```


2)
```

cat /etc/apt/apt.conf.d/20dbus

```

gives

```

// Notify all clients to reload the cache
APT::Update::Post-Invoke-Success { "[ ! -f /var/run/dbus/system_bus_socket ] || /usr/bin/dbus-send --system --dest=org.debian.apt --type=signal /org/debian/apt org.debian.apt.CacheChanged || true"; };

```


3)
```

sudo start-stop-daemon -S --exec /usr/sbin/aptd -- -d

```

gives

```

16:26:16 AptDaemon [INFO]: Initializing daemon
16:26:16 AptDaemon.PackageKit [DEBUG]: Use XAPIAN for the search
Traceback (most recent call last):
  File "/usr/sbin/aptd", line 28, in <module>
    aptdaemon.core.main()
  File "/usr/lib/python2.7/dist-packages/aptdaemon/core.py", line 2203, in main
    daemon = AptDaemon(options, bus=bus)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/core.py", line 1412, in __init__
    load_plugins)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 119, in __init__
    self._load_plugins()
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 125, in _load_plugins
    dists, errors = pkg_resources.working_set.find_plugins(env)
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 636, in find_plugins
    env = Environment(self.entries)
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 744, in __init__
    self.scan(search_path)
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 774, in scan
    self.add(dist)
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 794, in add
    if self.can_add(dist) and dist.has_version():
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 2391, in has_version
    self.version
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 2179, in version
    for line in self._get_metadata('PKG-INFO'):
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 2221, in _get_metadata
    for line in self.get_metadata_lines(name):
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 1536, in get_metadata_lines
    return yield_lines(self.get_metadata(name))
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 1529, in get_metadata
    f = open(self.path,'rU')
IOError: [Errno 2] No such file or directory: '/usr/local/lib/python2.7/dist-packages/ConnPlotter*.egg-info

```



4)
```

ls -l /etc/dbus-1/system.d/org.debian.apt.conf

```

gives

```

// Notify all clients to reload the cache
-rw-r--r-- 1 root root 434 Feb 11  2009 /etc/dbus-1/system.d/org.debian.apt.conf

```


5)
```

ls -l /etc/dbus-1/system.d/org.debian.apt.conf

```

gives

```

<!DOCTYPE busconfig PUBLIC
 "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>

  <policy user="root">
    <allow own="org.debian.apt"/>
  </policy>

  <policy context="default">
    <allow send_interface="org.debian.apt"/>
    <allow send_interface="org.debian.apt.transaction"/>
    <allow send_destination="org.debian.apt"/>
  </policy>

</busconfig>

```

Thanks for the kind help

---

### Post by schragge on 2013-02-26
Try to reinstall all aptdaemon-related stuff
```

sudo apt-get --reinstall --only-upgrade install aptdaemon\*

```

---

### Post by matt_symes on 2013-02-26
Hi

I think we are closing in on this now.

Some sanity checks

```
dpkg -l python2.7
``````
ls -l /usr/local/lib/python2.7/dist-packages/
```Interestingly enough in xubuntu

```
matthew-S206:/var/log % ls -l /usr/local/lib/python2.7/dist-packages/ 
total 0
matthew-S206:/var/log % 
```EDIT: Reinstalling the package maybe the quick fix so try that first

Kind regards

---

### Post by lalorca on 2013-02-26
Hi,

I did not yet try to re-install aptdaemon, I will do it after if this is confirmed from the outputs that Matt asked:

When typing
```

dpkg -l python2.7

```

I get
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  python2.7      2.7.3-0ubuntu3 Interactive high-level object-oriented langu

```




When typing
```

ls -l /usr/local/lib/python2.7/dist-packages/

```

I get
```

total 24
drwxr-sr-x  3 root staff 4096 Nov 23 21:26 ConnPlotter
-rw-r--r--  1 root staff  341 Nov 23 21:26 ConnPlotter-0.7a-py2.7.egg-info
lrwxrwxrwx  1 root staff   38 Nov 23 21:26 ConnPlotter*.egg-info -> ../site-packages/ConnPlotter*.egg-info
drwxr-sr-x  4 root staff 4096 Nov 23 21:26 nest
-rw-r--r--  1 root staff  248 Nov 23 21:26 PyNEST-2.0.0-py2.7.egg-info
lrwxrwxrwx  1 root staff   33 Nov 23 21:26 PyNEST*.egg-info -> ../site-packages/PyNEST*.egg-info
drwxr-sr-x 31 root staff 4096 Feb 11 09:59 sympy
-rw-r--r--  1 root staff 1185 Feb 11 09:59 sympy-0.7.2.egg-info

```




With
```

ls -l /usr/local/lib/python2.7/dist-packages/

```

I get
```

total 24
drwxr-sr-x  3 root staff 4096 Nov 23 21:26 ConnPlotter
-rw-r--r--  1 root staff  341 Nov 23 21:26 ConnPlotter-0.7a-py2.7.egg-info
lrwxrwxrwx  1 root staff   38 Nov 23 21:26 ConnPlotter*.egg-info -> ../site-packages/ConnPlotter*.egg-info
drwxr-sr-x  4 root staff 4096 Nov 23 21:26 nest
-rw-r--r--  1 root staff  248 Nov 23 21:26 PyNEST-2.0.0-py2.7.egg-info
lrwxrwxrwx  1 root staff   33 Nov 23 21:26 PyNEST*.egg-info -> ../site-packages/PyNEST*.egg-info
drwxr-sr-x 31 root staff 4096 Feb 11 09:59 sympy
-rw-r--r--  1 root staff 1185 Feb 11 09:59 sympy-0.7.2.egg-info

```


I have indeed been installing some neural modeling tools that are appearing there.


I was not expecting this much help! Thanks!

---

### Post by matt_symes on 2013-02-26
Hi

Read this.

[http://www.usr-local-share.com/?p=594](http://www.usr-local-share.com/?p=594)

It's your problem.

Kind regards

---

### Post by lalorca on 2013-02-26
Many thanks again to both of you !

Laureline

---

### Post by matt_symes on 2013-02-26
Hi

If you need any help in deciphering that article then just post back.

Either [[COLOR=#000000]schragge[/COLOR]]("http://ubuntuforums.org/member.php?u=1783515") or i will be able to help you.

Kind regards

---

