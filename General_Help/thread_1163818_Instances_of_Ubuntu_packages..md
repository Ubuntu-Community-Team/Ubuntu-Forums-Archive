---
title: "Instances of Ubuntu packages."
date: 2009-05-19
forum: General Help
---

### Post by switcha on 2009-05-19
Hi folks,

Can somebody please point me in the direction of finding out where old/archived instances of ubuntu packages might be stored for download?

I am having a problem with network-manager not installing because one the dependancy packages I have re-installed are not the correct versions.

Any help would be good.

Cheers.

---

### Post by Lampi on 2009-05-19
/var/cache/apt/archives

you can install it using dpkg -i <package name>.deb

---

### Post by switcha on 2009-05-19
Hi,

Assuming I can't connect my ubuntu machine to the internet - is there a url I can go to, to download an archived packaged?

Cheers.

---

### Post by kpkeerthi on 2009-05-19
If you look in /etc/apt/source.list, the repository configuration file, you will find lines like these:
```
deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted

```

Notice that these are standard HTTP URLs. Just copy/paste the URL to firefox and navigate into the **pool** folder.

---

### Post by switcha on 2009-06-05
Hi,

Thanks for your response.

Switch.

---

### Post by markharding557 on 2009-06-05
ubuntu package search in firefox you can manually download pacages there

---

