---
title: "How to change/use LC_TIME in Gnome 3 locale"
date: 2018-03-28
forum: Desktop Environments
---

### Post by ch6574 on 2018-03-28
Hello,

I'm running Ubuntu 17.10, and in a bash session I have the following:

```
$ locale
LANG=en_US.UTF-8
LANGUAGE=en_US:en
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC=en_US.UTF-8
LC_TIME=en_DK.UTF-8
LC_COLLATE="en_US.UTF-8"
LC_MONETARY=en_US.UTF-8
LC_MESSAGES="en_US.UTF-8"
LC_PAPER=en_US.UTF-8
LC_NAME=en_US.UTF-8
LC_ADDRESS=en_US.UTF-8
LC_TELEPHONE=en_US.UTF-8
LC_MEASUREMENT=en_US.UTF-8
LC_IDENTIFICATION=en_US.UTF-8
LC_ALL=

$ date +%x
2018-03-28

```

Notice that I have LC_TIME set to ISO8601 format. Works great on the command line.

Problem is I can't get Gnome 3 to use this setting. Everything in the GUI is in US date format.

**How can I change Gnome's time format?**

"gnome-control-center region" doesn't offer enough granularity.

Thanks!

---

