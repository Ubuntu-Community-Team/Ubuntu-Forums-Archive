---
title: "Generate iso-8859-1 locales?"
date: 2006-07-27
forum: Desktop Environments
---

### Post by kikinovak on 2006-07-27
Hi,

Some of the software that comes with Ubuntu (universe) is badly encoded, like dvdrip or audacity. I had encountered a similar problem on CentOS 4.3, where I solved the problem in a quick & dirty way: for example, edit /usr/share/applications/audacity.desktop like this:
Exec=sh -c 'LANG=fr_FR ; audacity'

Now a stock Ubuntu system only contains UTF-8 locales. I vaguely remembered (from having worked on Debian a few years ago) that I could use 'dpkg-reconfigure locales'. Tried this, but it only recreated en*** and fr*** locales in UTF-8, without giving me the option of creating other ones, say iso-8859-1 or iso-8859-15 as well. I wonder how I could do this.

Any suggestions?

---

