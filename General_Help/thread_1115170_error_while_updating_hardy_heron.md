---
title: "error while updating hardy heron"
date: 2009-04-03
forum: General Help
---

### Post by Rishinature on 2009-04-03
I am getting this error,every time I am trying to update my hardy heron. This happened after I installed a software called ejector from "http://www.getdeb.net/search.php?keywords=ejecter"


W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures were invalid: BADSIG 665F9AEFE1098513 Launchpad PPA for Julien Lavergne

---

### Post by kanikilu on 2009-04-03
If you installed ejector with a single "deb" package, it wouldn't have affected your apt sources file.

> Launchpad PPA for Julien Lavergne

Searching for that PPA, I think the following should fix it:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com E1098513
```

You should probably update the repository information after that to make sure it worked:

```
sudo apt-get update
```

---

### Post by Rishinature on 2009-04-03
Thnaks for the help. I followed the steps mentioned by you. I am still getting the following error
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures were invalid: BADSIG 665F9AEFE1098513 Launchpad PPA for Julien Lavergne
W: You may want to run apt-get update to correct these problems

However running apt-get update did not solve the problem.

---

### Post by kanikilu on 2009-04-04
I'm not sure...I don't normally use that repository, but I just tried it and it seems to work. 

Maybe try deleting it and re-adding:
```
sudo apt-key del E1098513
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com E1098513
sudo apt-get update
```

---

### Post by Rishinature on 2009-04-04
Thanks. I removed it.:p

---

