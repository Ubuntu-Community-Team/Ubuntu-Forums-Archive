---
title: "how do i change default text editor to nedit"
date: 2012-06-02
forum: Desktop Environments
---

### Post by honestann on 2012-06-02
[FONT=Book Antiqua]The default text editor in ubuntu 12.04 is gedit.  I much prefer nedit, and installed nedit on my system.  Now, how do I tell ubuntu nedit is the default text editor so nedit gets run instead of gedit when I open a text file?[/FONT]

---

### Post by LiamOS on 2012-06-02
```
# update-alternatives --config editor
```This may not work for graphical editors such as gedit or nedit, though. I can't say because I only ever use vim.


[Here]("http://dougsland.livejournal.com/51568.html")'s a way of changing vi to run vim instead, which may be easily reworked to change gedit use to nedit. *It may not work, and may cause some wreckage in your system*, so definitely check out how gedit ties into your system and what's actually going on before doing that.

A worthwhile command to run would be
```
# apt-get -s remove gedit
```as this will show you what other packages(if any) *would be* removed if you were to remove gedit, since the -s flag makes apt-get only pretend to perform the action.


EDIT: Alternatively, see this thread outlining what seems to be exactly what you want. [http://ubuntuforums.org/showthread.php?t=299086](http://ubuntuforums.org/showthread.php?t=299086)

---

### Post by mitchhhy on 2012-06-29
cp /usr/bin/gedit /usr/bin/gedit.save
ln -s /usr/bin/(ur edidtor) /usr/bin/gedit

:guitar:

---

