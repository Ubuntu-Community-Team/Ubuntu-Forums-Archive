---
title: "Stepmania on 12.10"
date: 2012-11-11
forum: Gaming &amp; Leisure
---

### Post by cabbage on 2012-11-11
Hi,

I've been happily running Stepmania on Ubuntu for years. Having recently performed an upgrade from 12.04 to 12.10 I've just discovered that Stepmania no longer works:

[INDENT]StepMania 3.9
Log starting 2012-11-11 15:07:47

(stepmania:4335): GLib-CRITICAL **: PCRE library is compiled without UTF8 support

(stepmania:4335): GLib-CRITICAL **: g_regex_match_full: assertion `regex != NULL' failed

StepMania has crashed.[/INDENT]

I've tried using the previous version of libpcre but this did not help.

I've also tried running Stepmania 5.0 alpha 3, but that just complains that it can't find libpng15.so.15. Search as I might, I've not found a package for this.

Has anyone else got any version of Stepmania working on 12.10?


Thanks,

Cabbage.

---

### Post by chiefofthejojos on 2012-12-02
I managed to get it working with the GetDeb Games PPA:
```

wget -q -O - http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add - sudo sh -c 'echo "deb http://archive.getdeb.net/ubuntu quantal-getdeb games" >> /etc/apt/sources.list.d/getdeb.list'
sudo apt-get update && sudo apt-get install sm-ssc

```

---

### Post by cabbage on 2012-12-20
I've managed to find teh getdeb packages from an ftp site, as the main site seems to be dead.

However, I still get the same crash and errors.

I'm running kubuntu 12.10 32 bit if that makes any difference.

---

### Post by cabbage on 2013-01-01
Not wanting to give in too easily, I apt-got the source for libpcre and rebuilt it ensuring the --enable-utf option was specified. However, this was one of the options used to build the package so wasn't likely to make much difference.

Unfortunately pcretest is no longer included so I couldn't test to see what compile options had been used to build it.

So, I then downloaded the latest source and built it making sure it had utf support and tested with pcretest.

I modified my library search path and used strace to ensure stepmania was picking up the new library.

But guess what... it still fails with the same message (no utf suport).

Clearly pcre is built correctly but something else is amiss here, but I don't know what.

The only option I have now is to wait until 13.04 and hope it magically gets fixed.

Its at times like these I start thinking about switching to freebsd... ;)

---

### Post by steelsnake on 2013-02-12
Sorry for replying to this old post... one solution for this problem is to delete/remove/rename the .gtkrc-2.0 file from your home directory. It affects quite a few games.

---

### Post by cabbage on 2013-03-04
I've had a problem with Citrix which has just been solved ([http://ubuntuforums.org/showthread.php?t=2073319](http://ubuntuforums.org/showthread.php?t=2073319)).

Turns out changing the Gtk configuration in KDE has also fixed my stepmania problems. Somehow I missed steelsnake's suggestion, but I think he was right.

---

