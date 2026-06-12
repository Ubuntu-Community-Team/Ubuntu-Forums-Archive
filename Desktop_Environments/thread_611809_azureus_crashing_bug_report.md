---
title: "azureus crashing bug report"
date: 2007-11-13
forum: Desktop Environments
---

### Post by themoebius on 2007-11-13
Azureus is stuck in some mode where it crashes every time I try to start it up. Here's what I get in the console:

```

zac@zac-desktop:~$ azureus
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
should load blocklist from: http://www.bluetack.co.uk/config/spconfig.txt
Retrieving data from: http://www.bluetack.co.uk/config/splist.zip
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb478674b, pid=15590, tid=3084446608
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0_03-b05 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0xb74b]
#
# An error report file with more information is saved as hs_err_pid15590.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)

```

I know I could just delete my ~/.azureus directory, but this has happened to me before and I'd rather just fix the problem. Is it an azureus bug or java bug or what?

I have attached hs_err_pid15590.log here.

---

### Post by felker2 on 2007-11-13
Are you using the most recent Azureus (3.0.3.4)?

---

### Post by themoebius on 2007-11-13
No, I'm using the latest in the Gutsy repositories, which I think is only 2.5.0.0

---

### Post by osric on 2007-11-13
You can get Azureus 3.0.3 from GetDeb:
[http://www.getdeb.net/app.php?name=Azureus](http://www.getdeb.net/app.php?name=Azureus)

---

### Post by felker2 on 2007-11-13
> **themoebius said:**
> No, I'm using the latest in the Gutsy repositories, which I think is only 2.5.0.0
Well, I had crashes with Azureus 2.5 on Gutsy. After upgrading to Azureus 3.x, everything worked great.

Upgrading to Azureus 3.0 is easy: download Azureus from [http://azureus.sourceforge.net/download.php?os=1]("http://azureus.sourceforge.net/download.php?os=1")
bunzip2 it, tar xvf it, and the use it.

HTH

---

### Post by themoebius on 2007-11-15
The new version hasn't crashed on me yet, but I haven't tested it extensively.

It is disturbing that the package in the repositories is so out of date. I hate installing these custom packages because it usually causes a big mess.

---

