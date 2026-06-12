---
title: "Discussion - https://help.ubuntu.com/community/slrn"
date: 2012-12-23
forum: Documentation and Community Wiki Discussions
---

### Post by andrew.46 on 2012-12-23
The usenet newsreader slrn had had a major update t0 1.0.1 as of December 21st 2012 and I have updated the Community Docs page with instructions for building this latest version:

[https://help.ubuntu.com/community/slrn](https://help.ubuntu.com/community/slrn)

See you all on usenet :)

---

### Post by andrew.46 on 2012-12-31
A quick note to slrn users: there is currently some confusion with the slrn website(s). The site I give in the wiki article:

Home of the slrn newsreader
[http://slrn.sourceforge.net](http://slrn.sourceforge.net)

is the one that I personally maintain for JED and it is up to date with details of the new version. There is another site which was formerly mirrored from the sourceforge site:

Home of the slrn newsreader
[http://www.slrn.org](http://www.slrn.org)

whose domain name has been recently purchased by somebody unattached to the slrn project. Unfortunately this site is somewhat out of date and does not contain information regarding the latest release. Hopefully this situation can be resolved soon...

---

### Post by andrew.46 on 2013-03-03
A small update for the slrn page, looks like the instructions for compiling the latest release version failed as Ubuntu some time ago moved libslang files around. This should capture both 32 and 64bit:

```

./configure --with-slrnpull --enable-setgid-code [COLOR="#FF0000"]--with-slang=/lib/*-linux-gnu[/COLOR]

```

Let me know of any problems with this one....

---

### Post by andrew.46 on 2013-03-08
slrn fanatics with a Windows 8 VM may also be interested in some work I have just completed:

Compiling the git slrn under Windows 8
[http://www.andrews-corner.org/slrn-windows.html](http://www.andrews-corner.org/slrn-windows.html)

This not only gets slrn running under Windows but it has a good look at some parts of the slrn source which will benefit Ubuntu users as well. And it is a lot of fun as well :)

---

### Post by andrew103 on 2014-03-17
i really needed this for the x64 bits platform.

---

### Post by andrew.46 on 2014-10-02
I no longer run slrn under Ubuntu but keen Usenet followers will be interested to hear that JED has released slrn 1.0.2 on pretty close to the 20th anniversary of slrn. [The announcement ]("https://groups.google.com/forum/#!topic/news.software.readers/E6vLYcJJ45s")has a nice acknowledgement of yours truly which was deeply appreciated...

Maybe see some of you on news.software.readers or alt.os.linux.ubuntu? I have cut back my Usenet time as Usenet slowly dies but there is still some life there :).

---

