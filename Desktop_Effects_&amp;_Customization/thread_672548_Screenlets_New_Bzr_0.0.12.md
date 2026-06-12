---
title: "Screenlets New Bzr 0.0.12"
date: 2008-01-19
forum: Desktop Effects &amp; Customization
---

### Post by Whise on 2008-01-19
Older Versions from repo or debs must be removed

[[IMG]http://img99.imageshack.us/img99/2658/733461dk9.th.jpg[/IMG]](http://img99.imageshack.us/my.php?image=733461dk9.jpg)
[[IMG]http://img182.imageshack.us/img182/9687/capturaecrascreenletsmasu2.th.png[/IMG]](http://img182.imageshack.us/my.php?image=capturaecrascreenletsmasu2.png)

Deb package - [http://gnome-look.org/content/download.php?content=73346&id=1&tan=40491514](http://gnome-look.org/content/download.php?content=73346&id=1&tan=40491514)
source - [http://gnome-look.org/content/download.php?content=73346&id=2&tan=70491650](http://gnome-look.org/content/download.php?content=73346&id=2&tan=70491650)
bzr - ```
https://code.launchpad.net/~screenlets-dev/screenlets/trunk
```





**Changes from 0.0.10**

Non composite support 
Improved screenlets manager
a milion bug fixes
third party screenlets
lots of new features

---

### Post by Whise on 2008-01-20
Note : if someone could buid a deb package i would be much apreciated

---

### Post by Whise on 2008-01-20
added a deb package [http://www.mediafire.com/?6nleuzmgegd](http://www.mediafire.com/?6nleuzmgegd)

---

### Post by Espreon on 2008-01-20
Hmmm, I think I will try this out when I get on my lappy...

---

### Post by oodlesOfmoodles on 2008-01-23
Amazing job! 0.0.10 was cool but nearly unusable. 0.0.12 is easy and fun to use!

Thanks so much for your hard work!

---

### Post by Whise on 2008-01-27
thanks , i added a new deb package

---

### Post by Whise on 2008-01-29
added new version

---

### Post by jamesey on 2008-01-29
is there a repository with 0.0.12?

---

### Post by Whise on 2008-01-30
not yet, there will be

---

### Post by tgecho on 2008-01-31
A little note for anyone that had a previous version installed at any time. Be sure to remove leftover config files before trying to launch this newer one. The manager kept looping around and repeatedly launching itself and I didn't know a good way to stop it short of relogging... so yeah, that was nasty.

The config stuff is stored in "/home/yourusername/.config/Screenlets/"

---

### Post by jamesey on 2008-01-31
> **Whise said:**
> not yet, there will be

hey Whise, are you in talks with the original creator of screenlets? he seems to have dropped off the face of the Earth.

---

### Post by Whise on 2008-02-01
he hasnt replied in a while ... 

branch now merged in trunk

---

### Post by plun on 2008-02-02
Helping whise a little,  a PPA is up for Screenlets.

Remove earlier version

```

sudo apt-get remove --purge screenlets
```

If Screenlets-new is installed

```
cd screenlets-new

sudo make uninstall

sudo rm -rf /usr/lib/python2.5/site-packages/screenlets*
```

Add repo

Menu System > Administration > Program sources > 3rd party tab > add

```
deb http://ppa.launchpad.net/gilir/ubuntu gutsy main universe
```

Install from terminal or use Synaptic and search for screenlets

```

sudo apt-get update && sudo apt-get install screenlets

Package must be manually verified  "y"   ( Launchpad "bug")

screenlets-manager
```


Direct URL to debfile
[http://ppa.launchpad.net/gilir/ubuntu/pool/main/s/screenlets/](http://ppa.launchpad.net/gilir/ubuntu/pool/main/s/screenlets/)

---

### Post by santiagoward2000 on 2008-02-02
Wow! This version of **Screenlets** is really cool! :)

> **plun said:**
> Helping whise a little,  a PPA is up for Screenlets.

Thanks for that repo!

Just one small thing: Is it necessary to have the **Autostart** folder on the Desktop? I'd rather have it in my Home directory (it kind of bothers me seeing it on the Desktop).
Thanks again! :KS

---

### Post by Whise on 2008-02-03
are you on xfce?

---

### Post by Gourgi on 2008-02-04
hi , i noticed that the latest stable revision is bzr-169 
can someone provide a amd64.deb for this revision ?
thanks in advance 

btw new screenlets rock ! :guitar:

will they be included in hardy ?

---

### Post by santiagoward2000 on 2008-02-04
> **Whise said:**
> are you on xfce?

Yes I am... Is there any problem?

---

### Post by santiagoward2000 on 2008-02-12
Hi!
I noticed the repository's version is **rev 165**. Will the final release (rev 174) be uploaded to it?

---

### Post by andrewsomething on 2008-02-13
[http://ppa.launchpad.net/gilir/ubuntu/pool/main/s/screenlets/](http://ppa.launchpad.net/gilir/ubuntu/pool/main/s/screenlets/)

You want: screenlets_0.0.12-0ubunutu1~ppa1_all.deb  from the above

---

### Post by santiagoward2000 on 2008-02-13
> **andrewsomething said:**
> [http://ppa.launchpad.net/gilir/ubuntu/pool/main/s/screenlets/](http://ppa.launchpad.net/gilir/ubuntu/pool/main/s/screenlets/)

You want: screenlets_0.0.12-0ubunutu1~ppa1_all.deb  from the above

Hi!
Thanks, but are you sure? According to [https://code.launchpad.net/~screenlets-dev/screenlets/trunk]("https://code.launchpad.net/~screenlets-dev/screenlets/trunk")
rev 174 was released on **2008-02-08**, and the file you say was last modified on **06-Feb-2008**.

---

### Post by Metallinut on 2008-02-13
Can anyone help me?  I was running screenlets 0.0.10, and upgraded to 0.0.12.

I used the repo method. I used Synaptic (GUI) to "completely remove" it.  Then added the repo, and installed again via GUI Synaptic.

I rebooted, and when it camb back up, my theme looked totally different.  The fonts and colors changed...almost looks more KDE-ish...and screenlets now will not run.  
If I go to System -> Preferences -> Appearance, an error pops up saying:
Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some
preferences may not take effect.  This could indicate a problem
with Bonobo, or a non-GNOME (e.g. KDE) settings manager
may already be active and conflicting with the GNOME settings
manager.

If I try and run screenletsd --gui in a terminal window I get this:
```
jp@lappy3000:~/.screenlets$ screenletsd --gui
Loading Daemon
It looks like you are running gnome
Traceback (most recent call last):
  File "/usr/share/screenlets-manager/screenlets-daemon.py", line 387, in <module>
    daemon = ScreenletsDaemon()
  File "/usr/share/screenlets-manager/screenlets-daemon.py", line 56, in __init__
    session_bus = dbus.SessionBus()
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 218, in __new__
    mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 107, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 121, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-5kA8NfpjUu: Connection refused
/home/jp/.config/autostart/Screenlets Daemon.desktop
/home/jp/.config/autostart/screenlets-daemon.desktop
False
Starter already exists.
Traceback (most recent call last):
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 1198, in <module>
    app = ScreenletsManager()
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 265, in __init__
    self.lookup_daemon()
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 313, in lookup_daemon
    self.daemon_iface = self.get_daemon_iface()
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 348, in get_daemon_iface
    bus = dbus.SessionBus()
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 218, in __new__
    mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 107, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 121, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-5kA8NfpjUu: Connection refused
jp@lappy3000:~/.screenlets$ 

```

I need to get this working again!!!  I followed the instructions!  The repo I used is [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) gutsy main universe.  and Synaptic says my screenlets version is 0.0.12~bzr165-1.  What happened?!?

---

### Post by Metallinut on 2008-02-13
Hah!  Never mind!  Just a newb!

I had installed new linux headers during the same uptime that I installed the new Screenlets.  I just rebooted again and all is well.

I love the new interface!  Got my desktop all tricked out just right!

Thanks!  

I just wish the slideshow screenlet could look recursively in picture folders!

---

