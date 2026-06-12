---
title: "firefox will not work correctly unless in sudo"
date: 2009-05-02
forum: General Help
---

### Post by rexxxlo on 2009-05-02
i just did the upgrade to 9.04 a few days ago and this morning i started having this problem

i am posting this from firefox sudo because i can not login or use the back buttons among other things im sure 

is there any ideas on how to fix this?

---

### Post by lovinglinux on 2009-05-02
Using Firefox with sudo is a very bad workaround, even temporarily. Install another browser like Epiphany to post and browse the web until you solve this problem. Epiphany is in the repositories, so you can use the Add/Remove manager to install it.

There is another thread about the a similar issue [here](http://ubuntuforums.org/showthread.php?t=1142293). No solution there yet.

---

### Post by BslBryan on 2009-05-02
Try simply changing the permissions of firefox.
```
sudo chown -R /home/your username/.mozilla/firefox
```

---

