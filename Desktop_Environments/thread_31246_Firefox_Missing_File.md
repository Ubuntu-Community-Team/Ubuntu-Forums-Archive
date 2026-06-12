---
title: "Firefox Missing File"
date: 2005-05-02
forum: Desktop Environments
---

### Post by elder68 on 2005-05-02
When I installed Firefox it works fine, I am using it now. However, whenerver I start it from the menu, where I put it, or from the terminal, a missing file flashes to the screen before Firefox loads. This file is:

/usr/share/ubuntu-artwork/home/index.html

When I cancel or close this missing file notice, Firefox loads and works OK.

If someone cold help me with the above I would appreciate it.

Thank you.

---

### Post by GeneralZod on 2005-05-02
This is nothing to worry about; Kubuntu's version of Firefox has the mentioned URL set as its default homepage, and the file is missing (I have the same).  Just change you Firefox Home Page (Edit->Preferences->General->Location) to something else (e.g. [www.google.com](www.google.com)) and the warning will disappear :)

---

### Post by syltty on 2005-05-02
$ apt-file search /usr/share/ubuntu-artwork/home/index.html
ubuntu-artwork: usr/share/ubuntu-artwork/home/index.html

sudo apt-get install ubuntu-artwork

should fix it

---

### Post by elder68 on 2005-05-02
> **GeneralZod]This is nothing to worry about said:**
> www.google.com[/url]) and the warning will disappear :)

Thank you, that was simple. Wish everything was that way. :)

---

### Post by elder68 on 2005-05-02
[QUOTE=syltty]$ apt-file search /usr/share/ubuntu-artwork/home/index.html
ubuntu-artwork: usr/share/ubuntu-artwork/home/index.html

sudo apt-get install ubuntu-artwork

should fix it[/QUOTE]

Thank you, I will update Firefox.

---

