---
title: "Adobe Reader 7.0.5 won't start"
date: 2006-06-03
forum: Desktop Environments
---

### Post by bsun on 2006-06-03
Fresh Dapper,

I just downloaded adobe reader and installed but after type acroread , nothing happened.  using pgrep acroread gives me no result.

I tried apt-cache acroread, but there is no acroread in repository. 


Any similiar problem?

P.S., I must use acrobe reader, evince is not an option for me currently.

---

### Post by desperado666 on 2006-06-03
install "libstdc++5"

---

### Post by bsun on 2006-06-03
:confused: 

~$ sudo apt-get install libstdc++5
Password:
Reading package lists... Done
Building dependency tree... Done
libstdc++5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by frying_fish on 2006-06-03
bsun, acroread is in multiverse, you will need to enable that repository first (either by editing /etc/apt/sources.list) or by adding the repository in synaptic, then you can get it from there.

---

### Post by bsun on 2006-06-05
Oh, :-), Thanks. I think I have solved this problem by refering to 

[http://www.scim-im.org/wiki/faq/gtk_gnome/why_firefox_mozilla_acrobat_reader_7_other_gtk_2_based_apps_can_not_be_installed_started](http://www.scim-im.org/wiki/faq/gtk_gnome/why_firefox_mozilla_acrobat_reader_7_other_gtk_2_based_apps_can_not_be_installed_started)

---

### Post by bsun on 2006-06-05
By the way, in dapper, I think there is no acroread in multiiverse rep...

---

