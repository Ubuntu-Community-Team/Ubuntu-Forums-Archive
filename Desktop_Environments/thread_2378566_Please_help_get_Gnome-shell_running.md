---
title: "Please help get Gnome-shell running"
date: 2017-11-24
forum: Desktop Environments
---

### Post by nickdc on 2017-11-24
I'm using a fairly recently installed Ubuntu-Gnome 16.04LTS. In order to get a particular application to function correctly I require the Gnome extension TopIcons to be installed. I've spent hours trying to do this and keep ending up with messages implying the gnome shell is not running, even though when I try to reinstall it I get the response that the latest version is already installed. The last thing I did, after further reading, was to run some commands, the output of which seem to indicate that gnome shell is not fully or properly installed. But I'm out of my depth trying to interpret this output:

```
nick@nick-build-1:~$ gnome-shell version
org.gnome.Shell already exists on bus and --replace not specified
nick@nick-build-1:~$ dpkg -l libgnome2-common
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
rc  libgnome2-comm 2.32.1-5ubun all          The GNOME library - common files
nick@nick-build-1:~$ dpkg -l gnome-shell
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  gnome-shell    3.18.5-0ubun i386         graphical shell for the GNOME des
nick@nick-build-1:~$ sudo gnome-tweak-tool
[sudo] password for nick: 
WARNING : Shell not installed or running
WARNING : Error detecting shell
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_group_shell_extensions.py", line 275, in __init__
    raise Exception("Shell not running or DBus service not available")
Exception: Shell not running or DBus service not available
WARNING : Shell not running
None
INFO    : GSettings missing key org.gnome.nautilus.desktop (key computer-icon-visible)
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
nick@nick-build-1:~$ 
```

I'm wary of making further interventions for fear of making matters worse. Please could someone who fully understands these matters kindly explain what I need to do?

---

### Post by deadflowr on 2017-11-25
What does 
```
env | grep XDG_CURRENT_DESKTOP
```
tell you is running?

---

### Post by nickdc on 2017-11-25
Thanks for coming to help, deadflowr

```

nick@nick-build-1:~$ env | grep XDG_CURRENT_DESKTOP
XDG_CURRENT_DESKTOP=GNOME-Flashback:Unity
nick@nick-build-1:~$ 
```

---

### Post by deadflowr on 2017-11-25
Well definitely not gnome-shell.
What options do you get when you try to switch sessions at the login screen?

---

### Post by nickdc on 2017-11-25
> **deadflowr said:**
> Well definitely not gnome-shell.
What options do you get when you try to switch sessions at the login screen?

Doh! I had completely forgotten that there were different options!! Must have known when I installed, as I was disappointed at the first login to get Unity-like GUI, so changed to Flashback. And that's what's been causing the problem, as to answer your question, I'm offered:

System Default
GNOME
GNOME Classic
*GNOME Flashback (Metacity)

I changed to GNOME and now I've been able to at last install TopIcons without any problem. Brilliant! Thanks so much for pointing out the obvious to me!
I'm just hoping that now it's installed it'll work on my preferred desktop, and it was just the installation that couldn't be done on Metacity. But that's for tomorrow; I need to shut down now for tonight. Again many thanks.

---

### Post by nickdc on 2017-11-26
Well, progress of sorts, but I'm more baffled than ever about Gnome and its many incarnations.

Of those four options (and what's the correct term for them: desktops? sessions? interface? GUI?) only GNOME gives me the icons I want in the top tray, but I really dislike the GNOME desktop environment in other respects. GNOME Classic is acceptable, but I don't get the icons. Maybe that's because I still need to do further configuring to get gnome-shell and /or TopIcons running, but I'm floundering here ... 

It would be a start to know if, theoretically at least, it should be *possible* to have tray icons fully functioning in all of these environments, as I don't want to spend much time pursuing the impossible! But if it's possible, it's worth the effort, as one learns along the way.

---

### Post by nickdc on 2017-11-27
I finally got there, though not sure exactly what was the key factor. But I'm now with my preferred desktop - GNOME Flashback (Metacity) - and the missing application icons are back in the top tray.

For the benefit of others, what I did was:

1. Log out and log back in choosing GNOME (from the little cog settings menu)
2. Install TopIcons Plus ([https://extensions.gnome.org/extension/1031/topicons/](https://extensions.gnome.org/extension/1031/topicons/))
3. Log back into Flashback, Alt+right-click on top panel, choose "Add to panel", choose "Notification area"
4. Restart the app of which the icons weren't appearing and - hey presto! - there they are!

Thanks for the help along the way.

---

