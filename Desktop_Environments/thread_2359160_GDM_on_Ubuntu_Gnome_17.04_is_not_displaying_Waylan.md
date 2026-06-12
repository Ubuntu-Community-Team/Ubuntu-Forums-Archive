---
title: "GDM on Ubuntu Gnome 17.04 is not displaying Wayland login option"
date: 2017-04-21
forum: Desktop Environments
---

### Post by sunre on 2017-04-21
I installed Ubuntu Gnome 17.04 and the nvidia binaries (through the Software&Updates > Additional Drivers interface). 

The issue is that the login screen does not offer any option for logging into Gnome with Wayland. I know there is support for the nvidia drivers and Gnome 3.24 shipped with Ubuntu should support this option. 

What should I look into for debugging this?

---

### Post by Dennis N on 2017-04-21
Did you have the Wayland option with the open source driver?

Using open source driver on Ubuntu Gnome 17.04, I have:


[B]Gnome
Gnome Classic
Gnome on Wayland[/B]

Also, we don't seem to have gtk+ version 3.24 on this release; I did read a while ago was going to ship 3.24.

```
dmn@Roxanne:~$ dpkg-query --list libgtk-3*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                      Version                   Architecture              Description
+++-=========================================-=========================-=========================-========================================================================================
ii  libgtk-3-0:amd64                          3.22.11-0ubuntu3          amd64                     GTK+ graphical user interface library
ii  libgtk-3-bin                              3.22.11-0ubuntu3          amd64                     programs for the GTK+ graphical user interface library
ii  libgtk-3-common                           3.22.11-0ubuntu3          all                       common files for the GTK+ graphical user interface library

```

EDIT: Found this out later: Gnome 3.24 does not mean it has gtk+ version 3.24 - the Gnome version number does not necessarily match the gtk + version it uses.

---

### Post by sunre on 2017-04-23
Thank you for your reply.

I tried switching to the open-source drivers and indeed the login screen now presents itself with the Wayland option. I was able to login and everything seemed fine. However I am forced to use the nvidia drivers (I am working with the nvidia cuda libraries).

I also tried setting **modeset=1** as suggested [here]("https://askubuntu.com/a/907839/528590"), to no effect.

Not sure how gtk and gnome versioning works, but most parts of gnome seem to be **3.24**:
```


ii  gnome-session                  3.24.0-0ubuntu1      amd64                GNOME Session Manager - GNOME 3 session
ii  gnome-session-bin              3.24.0-0ubuntu1      amd64                GNOME Session Manager - Minimal runtime
ii  gnome-session-canberra         0.30-3ubuntu1        amd64                GNOME session log in and log out sound events
ii  gnome-session-common           3.24.0-0ubuntu1      all                  GNOME Session Manager - common files
ii  gnome-settings-daemon          3.24.0-0ubuntu2      amd64                daemon handling the GNOME session settings
ii  gnome-settings-daemon-schemas  3.24.0-0ubuntu2      all                  gnome-settings-daemon schemas
ii  gnome-shell                    3.24.0-0ubuntu2      amd64                graphical shell for the GNOME desktop
ii  gnome-shell-common             3.24.0-0ubuntu2      all                  common files for the GNOME graphical shell
ii  gnome-shell-extensions         3.24.0-0ubuntu1      all                  Extensions to extend functionality of GNOME Shell
```

Any other suggestions? Are the nvidia drivers even supposed to work with Wayland?

---

### Post by sunre on 2017-04-23
Hmm, I did some more digging. Apparently there is a bug caused by different API's used by Nvidia and Wayland. More details [here]("https://www.reddit.com/r/linux/comments/66qyba/has_anyone_successfully_tried_gnome_324_and_got/") and [here]("https://github.com/Cloudef/wlc/pull/245").

---

