---
title: "Services running, ssh, mysql, apache?"
date: 2006-07-15
forum: Desktop Environments
---

### Post by detzx on 2006-07-15
I'm used to gentoo and bsd where nothing is installed from the start and I liked that because I knew what was on my system. With ubuntu I don't know what it installed and hwat holes are open.  How can I find this out?

---

### Post by MrHorus on 2006-07-15
sshd, apache and mysql are not installed by default so you won't have them running out of the box.

---

### Post by anthro398 on 2006-07-15
Point 1: Installed applications.  See System>Administration>Synaptic Package Manager

Point 2: Determining listening services.  'sudo netstat -natup | grep LISTEN' or submit to a [port scan]("https://www.grc.com/x/ne.dll?bh0bkyd2")

Point 3: Like Gentoo or BSD.  See [gentoo.org]("http://www.gentoo.org/") or [freebsd.org]("http://www.freebsd.org/").

---

