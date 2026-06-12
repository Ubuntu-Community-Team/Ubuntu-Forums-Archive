---
title: "Failed to Fetch/Download?"
date: 2009-01-11
forum: General Help
---

### Post by silverwolf636 on 2009-01-11
I am currently getting this message when I try to update:

Failed to fetch [http://ppa/launchpad.net/ssakar/ubuntu/dists/intrepid/main/binary-amd64/Packages.gz](http://ppa/launchpad.net/ssakar/ubuntu/dists/intrepid/main/binary-amd64/Packages.gz)  302 Found
Failed to fetch [http://ppa/launchpad.net/ssakar/ubuntu/dists/intrepid/main/source/Sources.gz](http://ppa/launchpad.net/ssakar/ubuntu/dists/intrepid/main/source/Sources.gz)  302 Found
Some index files failed to download, they have been ignored, or old ones used instead.

How can I correct this?

---

### Post by taurus on 2009-01-11
The site is either down or dead.  So, edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of those two lines to comment them out.  Save the changes and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by silverwolf636 on 2009-01-12
Are you saying to take the "failed to fetch" lines that I wrote out of sources.list?
If so, I cannot find them. I did a search and read the whole file and these lines do not exist.
I appreciate your assistance.

---

### Post by redbrain on 2009-01-12
You could go mad and enter a completly differnt set of apt-sources in their as-well but commenting out those 2 ones for now should be ok or just leave it for about a few hours and it should be dead on later :)

---

### Post by JohnWesleyMethodist on 2009-01-12
It appears that all or at least most of the "Software Sources" from Canada are no longer working. What's up? I tried an American server as well and that was down.

 I am suprised to see update servers like the University of Calgary not working. Why would this be?

---

### Post by avtolle on 2009-01-12
There could be a number of reasons; maintenance of the server being one. I'd try again in a few hours.

---

### Post by taurus on 2009-01-12
> **silverwolf636 said:**
> I am currently getting this message when I try to update:

Failed to fetch [http://ppa](http://ppa)**[COLOR="Red"]/[/COLOR]**launchpad.net/ssakar/ubuntu/dists/intrepid/main/binary-amd64/Packages.gz  302 Found
Failed to fetch [http://ppa](http://ppa)**[COLOR="Red"]/[/COLOR]**launchpad.net/ssakar/ubuntu/dists/intrepid/main/source/Sources.gz  302 Found
Some index files failed to download, they have been ignored, or old ones used instead.

How can I correct this?

By the way, I think you've made a typo in your /etc/apt/sources.list.

---

