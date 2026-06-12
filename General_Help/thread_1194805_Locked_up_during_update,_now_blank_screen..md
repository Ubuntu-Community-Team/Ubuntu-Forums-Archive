---
title: "Locked up during update, now blank screen."
date: 2009-06-23
forum: General Help
---

### Post by gonz037 on 2009-06-23
My Acer Aspire One netbook locked up during an update and now I am left with a black screen and my cursor. Right click does not work, Alt+F2 doesn't even work, pretty much the only thing I can do is hit print screen, click the help button, then get help online will open firefox. I can CTRL+ALT+F1 to get into terminal. I tried sudo apt-get update and sudo apt-get upgrade in the terminal to no avail. Any ideas? thanks

---

### Post by gonz037 on 2009-06-23
For anyone else that might have this problem I did the following from [http://www.neowin.net/forum/index.php?showtopic=646052&pid=589525923&st=0&#entry589525923](http://www.neowin.net/forum/index.php?showtopic=646052&pid=589525923&st=0&#entry589525923)

> 
$ sudo apt-get remove ubuntu-desktop
and then:
$ sudo apt-get install ubuntu-desktop
along with multiple:
$ sudo apt-get update
and
$ sudo apt-get upgrade


---

