---
title: "Synaptic update errors with Firefox/Mozilla-Firefox"
date: 2005-10-16
forum: Desktop Environments
---

### Post by libertyforever on 2005-10-16
Newbie here.  Trying to do update through Synaptic and continually get the following error:
[COLOR="Blue"]W: Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/mozilla-firefox_1.0.7-0ubuntu15_all.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/mozilla-firefox_1.0.7-0ubuntu15_all.deb)
  404 Not Found
W: Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/firefox_1.0.7-0ubuntu15_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/firefox_1.0.7-0ubuntu15_i386.deb)
  404 Not Found[/COLOR]
There doesn't seem to be a problem with Firefox.  I saw in other threads that there was mention of mozilla-firefox and firefox being too similiar and uninstalling one of them solved a different problem than I am having.  Any thoughts?

---

### Post by Leif on 2005-10-16
the mirrormax backports repositories have been shut down. use 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

instead

---

### Post by libertyforever on 2005-10-17
Thanks Leif for the help.  For those who may find this thread, I did some stuff that scared me to death through this process, but at the end, Firefox is working and no more errors in Synaptic.  My problem, as Leif said, is the mirrormax repositories are dead.  Read [_this_]("http://ubuntuforums.org/showthread.php?t=69681") to find out about it.  Then read _[this]("http://ubuntuforums.org/showthread.php?t=52168")_ to update your repositories.  Here's what I did.

sudo gedit /etc/apt/sources.list

When you get that open replace the mirrormax backports with what you will find at the second link above.

Thanks to all you out there who are willing to help us newbies!

---

