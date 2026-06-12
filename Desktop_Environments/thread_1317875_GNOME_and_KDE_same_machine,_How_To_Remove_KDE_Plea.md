---
title: "GNOME and KDE same machine, How To Remove KDE? Please Help."
date: 2009-11-07
forum: Desktop Environments
---

### Post by Aflack on 2009-11-07
simple..

i installed kde on my gnome using sudo apt-get install kubuntu-desktop.

it went well and i tried kde and dont like it so i did sudo apt-get uninstall kubuntu desktop. said it uninstalled...

i check and see all the kde apps are still there. so i reboot... and i still have the option to log on a kde session so i try it and kde is still fully working.

How do i remove it?? i tried sudo apt get remove kubuntu desktop again but it says its not installed. 

im confused, how do i remove  all the apps and kde?

---

### Post by XubuRoxMySox on 2009-11-07
try 

```
sudo apt-get purge kubuntu-desktop
```

Purge instead of "uninstall."

-Robin

---

### Post by alienclone on 2009-11-07
i have pasted this link in a few other threads on ubuntuforums.org , does nobody search for the answer on their own anymore??

this page will explain what to do  [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Aflack on 2009-11-07
> **alienclone said:**
> i have pasted this link in a few other threads on ubuntuforums.org , does nobody search for the answer on their own anymore??

this page will explain what to do  [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

[http://ubuntuforums.org/search.php?searchid=66422088](http://ubuntuforums.org/search.php?searchid=66422088)

didnt find it. and im using the command on the website.. hopefully it goes well

edit: worked so far. im going to reboot real quick... then i can say if it did what i wanted.. brb.
edit2: worked perfect thanks a lot.

---

### Post by alienclone on 2009-11-07
> **Aflack said:**
> [http://ubuntuforums.org/search.php?searchid=66422088](http://ubuntuforums.org/search.php?searchid=66422088)

didnt find it. and im using the command on the website.. hopefully it goes well

edit: worked so far. im going to reboot real quick... then i can say if it did what i wanted.. brb.
edit2: worked perfect thanks a lot.

yeah the search function on the forum website is crap.

use Google and enter "site:ubuntuforums.org" without quotes after your search terms..

eg.     completely remove KDE site:ubuntuforums.org

---

### Post by Kenijs on 2009-11-11
> **dixiedancer said:**
> try 

```
sudo apt-get purge kubuntu-desktop
```Purge instead of "uninstall."

-Robin

or 
```
sudo apt-get autoremove kubuntu-desktop
```

---

### Post by weishigoname on 2010-03-17
this really works

---

