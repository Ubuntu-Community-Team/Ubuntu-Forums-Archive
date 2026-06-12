---
title: "Cannot apt-get install libncursesw5-dev"
date: 2009-03-21
forum: General Help
---

### Post by zwanzig on 2009-03-21
I cannot apt-get install libncursesw5-dev
$ sudo apt-get install libncursesw5-dev
[...]
The following packages have unmet dependencies:
  libncursesw5-dev: Depends: libncursesw5 (= 5.6+20071124-1ubuntu2) but 5.6+20080419-2 is to be installed
E: Broken packages

What to do?

---

### Post by khelben1979 on 2009-03-21
Try
```
sudo apt-get install -f
```

to see if it can fix it.

---

### Post by zwanzig on 2009-03-21
No luck...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by khelben1979 on 2009-03-21
What package require you to have that installed?

---

### Post by zwanzig on 2009-03-22
despotify, when trying to link with ld -lncursesw

---

### Post by khelben1979 on 2009-03-22
Have you checked out [their homepage]("http://despotify.se/")? (see link)

---

### Post by mc4man on 2009-03-22
It appears your running intrepid but the version shown "but 5.6+20080419-2 is to be installed" isn't an intrepid version.
It actually looks like a version that would have been used in a jaunty alpha release

You may want to ck. in your sources.list, and also ck. in synaptic for the installed version of libncursesw5
```
cat /etc/apt/sources.list
```

for intrepid you want your libncursesw5 to be 5.6+20071124-1ubuntu2

If your running jaunty then the ver. is now 5.7+20090207-1ubuntu1

Here's where 5.6+20080419-2 is mentioned (early jaunty I believe

[https://launchpad.net/ubuntu/breezy/+source/ncurses/+changelog](https://launchpad.net/ubuntu/breezy/+source/ncurses/+changelog)

---

### Post by zwanzig on 2009-03-23
> **mc4man said:**
> It appears your running intrepid but the version shown "but 5.6+20080419-2 is to be installed" isn't an intrepid version.
It actually looks like a version that would have been used in a jaunty alpha release

You may want to ck. in your sources.list, and also ck. in synaptic for the installed version of libncursesw5
```
cat /etc/apt/sources.list
```

for intrepid you want your libncursesw5 to be 5.6+20071124-1ubuntu2

If your running jaunty then the ver. is now 5.7+20090207-1ubuntu1

Here's where 5.6+20080419-2 is mentioned (early jaunty I believe

[https://launchpad.net/ubuntu/breezy/+source/ncurses/+changelog](https://launchpad.net/ubuntu/breezy/+source/ncurses/+changelog)

You got it! Thank you. I downgraded libncursesw5 to 5.6+20071124-1ubuntu2 and it worked like a charm

---

