---
title: "403  Forbidden [IP: 143.95.32.90 80]"
date: 2019-04-09
forum: Desktop Environments
---

### Post by m.eraj1995 on 2019-04-09
dear sir, when hit sude apt-get update or upgrade i am getting below error,

Err:5 [http://www.getdeb.net/ubuntu](http://www.getdeb.net/ubuntu) $(lsb_release InRelease               
  403  Forbidden [IP: 143.95.32.90 80]

---

### Post by Holger_Gehrke on 2019-04-09
getdeb and its sister-site playdeb have a new owner who has removed the repositories and turned the sites into spam-filled pseudo-news sites. Simply remove playdeb from your package-sources and everything should be good again.

Holger

---

### Post by m.eraj1995 on 2019-04-09
thanks, sir i removed and its working fine.

---

### Post by achocolada on 2019-05-08
> **Holger_Gehrke said:**
> getdeb and its sister-site playdeb have a new owner who has removed the repositories and turned the sites into spam-filled pseudo-news sites. Simply remove playdeb from your package-sources and everything should be good again.

Holger

I have some problem too. Would you like please to tell me how to remove that "playdeb" ?

---

### Post by Holger_Gehrke on 2019-05-08
There a graphical tool named "Software & Updates" that should allow you to remove that repository. 

There's also the '-r' (remove) option to 'add-apt-repository' ('sudo add-apt-repository -r [http://www.getdeb.net/ubuntu](http://www.getdeb.net/ubuntu)').

Otherwise check the content of the file '/etc/apt/sources.list' or the files in the directory '/etc/apt/sources.list.d/'. If the reference to playdeb is in a file of its own then remove that file ('sudo rm /etc/apt/sources.list.d/name-of-the-file-with-playdeb-in-it') or use sudoedit to edit the file and either remove that line or put a comment-character ('#') at the beginning of that line.

Holger

---

