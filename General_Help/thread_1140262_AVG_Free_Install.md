---
title: "AVG Free Install"
date: 2009-04-27
forum: General Help
---

### Post by nichos on 2009-04-27
Installed AVG Free, installer details say is in "Utils" , I found utils in File System, but AVG is no where to be found.

can you help an absolute idiot on linux jargon?

Thanx  

[[IMG]http://img218.imageshack.us/img218/6038/47259353.th.png[/IMG]](http://img218.imageshack.us/my.php?image=47259353.png)

[[IMG]http://img219.imageshack.us/img219/8840/screenshotpackageinstal.th.png[/IMG]](http://img219.imageshack.us/my.php?image=screenshotpackageinstal.png)

---

### Post by Niniel on 2009-04-27
Mine (7.5) is located in /usr/bin, avggui is the executable.

Just opening a terminal window and entering "gksudo avggui" should also work (that's the command in the official shortcut, which I have in the Applications/Accessories menu).

---

### Post by nichos on 2009-04-28
Thanx,

"gksudo avggui"  after i enter password nothing happens & there's nothing in Applications.

This is what shows in usr/bin:-

[[IMG]http://img90.imageshack.us/img90/6401/screenshotfilebrowser.th.png[/IMG]](http://img90.imageshack.us/my.php?image=screenshotfilebrowser.png)

---

### Post by Niniel on 2009-04-28
Just figured out that those are all link... pointing to /opt... for 7.5 it was /opt/grisoft, for 8.5 it's /opt/avg

However, it looks like the package from the Grisoft site only installs the command line version.
According to the 7.5 manual, which is on the 8.5 download page, for a GUI, you need the file avggui-1.0-{release}.i386.deb, which can be had at [http://www.avg.com/us.download?prd=avl](http://www.avg.com/us.download?prd=avl).
That seems to be expecting an installation of 7.5 though... which is no longer available for download from Grisoft.
I'm not sure how to make the 7.5 gui work with 8.5. I've looked around the interwebs a bit and couldn't find anything, either, apart from unanswered questions about how to do it.

---

