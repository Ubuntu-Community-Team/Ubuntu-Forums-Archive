---
title: "Ubuntu/Vista question"
date: 2008-11-24
forum: Desktop Environments
---

### Post by cbo0485 on 2008-11-24
Wasn't sure how to quickly word the title, but here is my situation.  Wasn't sure on where this should be posted either.

Currently I have a computer(one physical computer) with the same hardware components, but two hard drives.  I originally only had one, and had Vista installed.  I have since connected the other one, and have ubuntu(hardy heron I believe - on the vista partition right now so no quick way to check).  I think 8.0.4. 

Anyways, I was wondering, is there a way that I can login to the Ubuntu OS, then easily mount the vista hard drive, and then pull over some files?  B/c I originally had my vista partition set up as a network drive, and I have a bunch of movies and music on there(did all this before I d/l ubuntu), but most recently my vista partition has decided to start crashing randomly.

So, I'd like to be able to login to Ubuntu, somehow access the Vista partition, and pull down some 150gb of music/movies.

Then, the second part would be, can anyone point me to an easy way to set up Ubuntu as a movie/music server so I can access all those files from my Windows XP Laptop?

---

### Post by taurus on 2008-11-24
Yes, you can mount your vista partition so you can access it from Ubuntu.  Just install ntfs-config and use it to configure your ntfs partition.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by cbo0485 on 2008-11-24
> **taurus said:**
> Yes, you can mount your vista partition so you can access it from Ubuntu.  Just install ntfs-config and use it to configure your ntfs partition.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

Thanks for that, I actually just logged in to my ubuntu partition, and was able to pull everything I needed.  Its still going, 150gb don't exactly transfer fast, even though it is going at 25 mb/s

So, what about setting up a directory in Ubuntu as a shared directory that I can access from a Windows XP Laptop?

---

