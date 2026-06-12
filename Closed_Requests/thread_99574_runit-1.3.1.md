---
title: "runit-1.3.1"
date: 2005-12-05
forum: Closed Requests
---

### Post by HippoMan on 2005-12-05
I'm requesting that runit-1.3.1 be ported to backports.

The author of the "runit" package is also a Debian developer, and he very rapidly makes Debian packages of his new versions and puts them into "sid".  Currently, that's version 1.3.1 of runit, although we have only version 1.2.3 in the Ubuntu repositories.

This newer version adds the new "sv" command which I now am using via the non-dpkg (tar.gz) build of runit-1.3.1 that I sadly have to make use of on my otherwise all "apt-get" based system.  Version 1.2.3 does not have this "sv" command.

Furthermore, there are a few other new features that were added between 1.2.3 and 1.3.1.

This 1.3.1 code is built with the same libraries and tools as the earlier version.

Given that runit-1.2.3 is already an official Ubuntu package, and given that 1.3.1 is an equally official Debian package (as was 1.2.3 several months ago), and given that there is indeed new functionality and no changes in its build or runtime requirements, the posting guidelines seem to indicate that version 1.3.1 is eligible to be ported to backports.

I hereby am making that request.

Thank you very much.

---

### Post by HippoMan on 2005-12-05
[quote=HippoMan]I'm requesting that runit-1.3.1 be ported to backports.[/quote]
P.S. -- The package runit-run is a companion to runit.  It's written by the same author and it also is up to date on Debian sid.  The latest version, runit-run-0.6.0, hasn't changed much from the 0.5.0 version that's currently available on Ubuntu, but this later version is needed for compatibility with runit-1.3.1.  Therefore, I hereby request this package, as well.  Thanks.

---

### Post by benplaut on 2005-12-05
what is runit? and alt+f2 sort of thing?

---

### Post by HippoMan on 2005-12-05
[quote=benplaut]what is runit? and alt+f2 sort of thing?[/quote] Well, no ... it's a GPL-based replacement for daemontools, which means that it serves a similar purpose as sysvinit and other similar schemes ... and in fact, it can replace sysvinit.  The author calls it "a UNIX init scheme with service supervision".  Details here: [http://smarden.org/runit/]("http://smarden.org/runit/")

---

### Post by benplaut on 2005-12-05
that's really cool :)

---

### Post by Seth on 2005-12-10
[QUOTE=HippoMan]I'm requesting that runit-1.3.1 be ported to backports.

The author of the "runit" package is also a Debian developer, and he very rapidly makes Debian packages of his new versions and puts them into "sid".  Currently, that's version 1.3.1 of runit, although we have only version 1.2.3 in the Ubuntu repositories.

This newer version adds the new "sv" command which I now am using via the non-dpkg (tar.gz) build of runit-1.3.1 that I sadly have to make use of on my otherwise all "apt-get" based system.  Version 1.2.3 does not have this "sv" command.

Furthermore, there are a few other new features that were added between 1.2.3 and 1.3.1.

This 1.3.1 code is built with the same libraries and tools as the earlier version.

Given that runit-1.2.3 is already an official Ubuntu package, and given that 1.3.1 is an equally official Debian package (as was 1.2.3 several months ago), and given that there is indeed new functionality and no changes in its build or runtime requirements, the posting guidelines seem to indicate that version 1.3.1 is eligible to be ported to backports.

I hereby am making that request.

Thank you very much.[/QUOTE]
Until official backports enter the repos, here you go:
[http://ubuntuforums.org/showthread.php?t=101736](http://ubuntuforums.org/showthread.php?t=101736)

---

### Post by jdong on 2005-12-12
So runit and runit-run?

---

### Post by HippoMan on 2005-12-12
[quote=jdong]So runit and runit-run?[/quote]
Yes, I'm requesting the two of them:  runit-1.3.1 and runit-run-0.6.0, both from Debian/sid.

Thank you very much.

---

### Post by jdong on 2005-12-12
Both sent to James.

(oh god now that annoying chris brown song is stuck in my mind.... AHHHHHHH)

---

### Post by HippoMan on 2005-12-21
[quote=jdong]Both sent to James.[/quote]
Thank you very much!  (sorry for the late reply ... I was out of town)

---

