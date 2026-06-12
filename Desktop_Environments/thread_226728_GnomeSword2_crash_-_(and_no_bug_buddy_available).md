---
title: "GnomeSword2 crash - (and no bug buddy available)"
date: 2006-07-31
forum: Desktop Environments
---

### Post by rolf_lindberg on 2006-07-31
I am trying to run GnomeSword2 Bible Study Program, but every time I try to run gnomesword2 it crashes. I tried running it as sudo, gksudo, just as it is in the menu when first installed, nothing helps. I tried installing in Breezy - didn't work. I tried upgrading to Dapper - didn't work. I tried a complete reinstall of Dapper - didn't work. I tried Dapper on a different computer - GnomeSword still won't start. And also, when Bug Buddy starts to report an error to the developers - GnomeSword isn't even there as an option to report an error from. I don't think anything will happen if I file my bug report to the nautilus people...

I really want to get this app working. Seems like in the forum posts there are people who succeeded, so how did you guys do it???

I found BibleTime, so that will do for now. But I would like to get GnomeSword to work too.

---

### Post by mlind on 2006-07-31
You can report bug about this to [https://launchpad.net/distros/ubuntu/+source/gnomesword/+bugs](https://launchpad.net/distros/ubuntu/+source/gnomesword/+bugs)
There seems to be two bugs about this same issue already

---

### Post by mlind on 2006-07-31
You can try if this works for you
[http://www.freefilehoster.com/uploads/1154378424gnomesword_2.1.7.tar.gz](http://www.freefilehoster.com/uploads/1154378424gnomesword_2.1.7.tar.gz)

---

### Post by sulobanks on 2006-07-31
I have gnomesword working on my dapper machine, but I had the same issue as you when I was running breezy.  What I figured out on breezy was to make sure I had one of each type of resource installed. e.g. At least one bible, commentary and dictionary.  If any of those panes was empty, that's when it would crash on me.  It's been running fine for me in dapper.

---

### Post by bradleesargent on 2007-07-03
I downloaded the source and compiled it using configure and make based on the instructions in 
[http://gnomesword.sourceforge.net/](http://gnomesword.sourceforge.net/)

I used to have problems with the studypad only because it caused gnomesword to crash.
After compiling it (installing the packages as necessary in the config.log file) it works fine.

---

