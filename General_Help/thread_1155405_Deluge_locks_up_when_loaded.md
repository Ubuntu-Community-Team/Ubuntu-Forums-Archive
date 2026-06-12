---
title: "Deluge locks up when loaded"
date: 2009-05-10
forum: General Help
---

### Post by matjoeman on 2009-05-10
Hey

My Deluge locks up as soon as I load it.  The window is only partially drawn with no buttons.

Here's what it says when i run it from terminal:

matthew@matthew-desktop:~$ deluge
1.1.7
/var/lib/python-support/python2.6/deluge/ui/gtkui/mainwindow.py:63: GtkWarning: gtk_toolbar_set_icon_size: assertion `icon_size != GTK_ICON_SIZE_INVALID' failed
  "glade/main_window.glade"))

I've tested it with the version from the jaunty repos (1.1.6) and from the deluge ppa (1.1.7) with no success.

Can anyone help me figure this out?

Thanks, Matthew

---

### Post by lovinglinux on 2009-05-11
Check your firewall settings. Deluge needs to connect to the daemon in the loopback device and if it can't it locks while loading.

If that doesn't work, then try changing the gtk theme. More info at [http://ubuntuforums.org/showthread.php?p=7210700](http://ubuntuforums.org/showthread.php?p=7210700)

---

### Post by blazemore on 2009-05-11
I've had success fixing problems like this by doing something like this:
```
sudo apt-get build-dep deluge
```

---

### Post by kpkeerthi on 2009-05-11
> **blazemore said:**
> I've had success fixing problems like this by doing something like this:
```
sudo apt-get build-dep deluge
```
That would just install the dev (source files) packages required to build deluge. I wonder how that fixed the issue for you. Strange.

---

### Post by lovinglinux on 2009-05-11
> **kpkeerthi said:**
> That would just install the dev (source files) packages required to build deluge. I wonder how that fixed the issue for you. Strange.

I agree. Probably not the solution.

---

### Post by blazemore on 2009-05-11
I don't care why, it just worked for me

---

### Post by matjoeman on 2009-05-12
Thanks for the replies, guys

I've never touched iptables so that's not it.

I flipped the gnome theme around a few times but that didn't work.

I removed python 2.5 but that didn't work.

I even tried the "sudo apt-get build-dep deluge" but that didn't work.

I'm pretty sure its a problem with python and its interaction with gtk, but I can't think of what to do to fix it.

---

### Post by kpkeerthi on 2009-05-12
Try removing ~/.config/deluge
**Warning: **You will loose all deluge settings by doing this. You may want to backup this folder first.

---

### Post by JTLJudoMan on 2009-05-13
I get exactly the same error:

 deluge
1.1.7
/var/lib/python-support/python2.6/deluge/ui/gtkui/mainwindow.py:63: GtkWarning: gtk_toolbar_set_icon_size: assertion `icon_size != GTK_ICON_SIZE_INVALID' failed
  "glade/main_window.glade"))


I have deleted all of the settings files in the .config/deluge folder... like ALL of them and tried again and it doesn't work.  I've re-installed, un-installed, pre-installed, and any other form of installed that I could think of and nothing seems to be helping.  Deluge just loads partially then goes grey.  Its definitely a problem with GTK interaction for some reason.

Any other things.  
Note: Previous user's post about build-dep deluge did not resolve the issue.

---

### Post by HittingSmoke on 2009-05-13
I also started getting this issue this morning after upgrading to Jaunty.

Not sure if it's at all relevant but... Before I did the Jaunty upgrade I ran the update manager which updated the kernel to something *.14 from *11.

After reboot from that update my grafics went nutty and wouldn't properly load X. I was getting some Nvidia error. The tried the "Reconfigure graphics settings for this hardware" which gave the same results, then chose "Reconfigure graphics setting for default settings" which let me get back to my desktop.

After I got everything back in order and my Nvidia drivers working properly again by updating to the newest beta (which I think fixed the problem by reconfiguring Xorg for me) I started the Jaunty upgrade process and went to make lunch. Upon reboot me default Kernel in grub was back to the previous *.11 version. This is when I noticed Deluge stop working so I'm not sure which step I took broke it.

I also get the error..

```
chris@chris-desktop:~$ deluge
1.1.6
/var/lib/python-support/python2.6/deluge/ui/gtkui/mainwindow.py:63: GtkWarning: gtk_toolbar_set_icon_size: assertion `icon_size != GTK_ICON_SIZE_INVALID' failed
  "glade/main_window.glade"))

```

..when trying to start from the terminal then it just locks up and nothing happens.

I've tried installing the version in the official Ubuntu repos (1.1.6) as well as version 1.1.7 from the Deluge PPA. Both have the same results other than the version number reported in the error message.

I also tried to compile 1.1.7 from source from the Deluge web site but received such a long list of errors I can't post it because in runs clear off my terminal history.

---

### Post by lovinglinux on 2009-05-14
Try updating Ubuntu. I saw a report on Deluge web site about the same issue, which was solved with recent updates (05/05/2009).

---

### Post by HittingSmoke on 2009-05-14
> **lovinglinux said:**
> Try updating Ubuntu. I saw a report on Deluge web site about the same issue, which was solved with recent updates (05/05/2009).

Ubuntu is up to date. The upgrade to Jaunty is what seems to have broken it, which would imply that my Ubuntu is up to date and I'm having the exact same problem with the latest versions of both Ubuntu and Deluge...

---

### Post by Trebaruna on 2009-05-14
The warning may well be unrelated. When I start Deluge from the terminal it also complains with that warning, and then proceeds to run just fine, so far as I can tell.

EDIT: Some useful info. I'm running 9.04 desktop, using deluge from the PPA, and as far as I know it's worked fine since 9.04RC. I have reinstalled 9.04 and carried over my settings, it's still working...

---

### Post by lovinglinux on 2009-05-14
Try this: [http://forum.deluge-torrent.org/viewtopic.php?f=7&t=16555](http://forum.deluge-torrent.org/viewtopic.php?f=7&t=16555)

---

### Post by HittingSmoke on 2009-05-14
> **lovinglinux said:**
> Try this: [http://forum.deluge-torrent.org/viewtopic.php?f=7&t=16555](http://forum.deluge-torrent.org/viewtopic.php?f=7&t=16555)

Wonderful! Thanks, that last command on that post did the trick, didn't need any of the other stuff because it was already installed with all dependencies from the PPA

```
sudo ln -s /usr/lib/python2.5/site-packages/libtorrent.so /usr/lib/python2.6/dist-packages
```

---

### Post by matjoeman on 2009-05-14
That line didn't work for me.  I've already installed all the versions of those packages from the repositories.

I don't even have a file at:

/usr/lib/python2.5/site-packages/libtorrent.so

---

### Post by hvbakel on 2009-05-14
I've had the same issue and I'm pretty sure it's caused by a failure to start deluged before the gui comes up. What works for me is to start deluge with the following shell script:

```
#!/bin/sh
/usr/bin/deluged
/usr/bin/deluge $*
```

---

### Post by kpkeerthi on 2009-05-14
Deluge (GUI) /usr/bin/deluge should autostart the daemon if "classic mode" is turned on. 
If classic mode is turned off, then the GUI will prompt to start/connect to the daemon.

---

### Post by matjoeman on 2009-06-07
So I've still been working on this and I figured out that the problem relates to how deluge imports the old torrent data from the persistent.state file into the new format.

When I run deluged -d I get this:
```

[ERROR   ] 12:31:36 main:207 'torrent_info' object has no attribute 'upload_rate_limit'
Traceback (most recent call last):
  File "/var/lib/python-support/python2.6/deluge/main.py", line 204, in start_daemon
    Daemon(options, args)
  File "/var/lib/python-support/python2.6/deluge/core/daemon.py", line 56, in __init__
    self.core = Core(options.port).run()
  File "/var/lib/python-support/python2.6/deluge/core/core.py", line 239, in run
    component.start()
  File "/var/lib/python-support/python2.6/deluge/component.py", line 198, in start
    _ComponentRegistry.start()
  File "/var/lib/python-support/python2.6/deluge/component.py", line 118, in start
    self.start_component(component)
  File "/var/lib/python-support/python2.6/deluge/component.py", line 125, in start_component
    self.start_component(depend)
  File "/var/lib/python-support/python2.6/deluge/component.py", line 130, in start_component
    self.components[name].start()
  File "/var/lib/python-support/python2.6/deluge/core/torrentmanager.py", line 190, in start
    deluge.core.oldstateupgrader.OldStateUpgrader()
  File "/var/lib/python-support/python2.6/deluge/core/oldstateupgrader.py", line 82, in __init__
    self.upgrade05()
  File "/var/lib/python-support/python2.6/deluge/core/oldstateupgrader.py", line 124, in upgrade05
    max_upload_speed=ti.upload_rate_limit,
AttributeError: 'torrent_info' object has no attribute 'upload_rate_limit'
```

I'm not sure whether that means that one of the torrent objects has upload_rate_limit missing or whether its not supposed to be there at all.  persistent.state isn't an easy file to read and edit by hand.

/var/lib/python-support/python2.6/deluge/core/oldstateupgrader.py doesn't seem to exist which is odd.

Does anybody have an idea for a workaround?

---

