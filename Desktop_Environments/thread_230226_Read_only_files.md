---
title: "Read only files"
date: 2006-08-05
forum: Desktop Environments
---

### Post by Mr_ on 2006-08-05
After recently installing ubuntu successfully after many attempts I'm trying to ease my way around.

I was initially frustrated with the fact that ubuntu would not automatically identify DNS nameservers, something I always took for granted with windows. After reading through a few HOWTO's I found out I could add it manually  by adding it to resolve.conf, right? Well I tried and failed as it's a read only file and it's owned by root, so I have to manually add it to the dns tab in Networking as for some reason the DNS addresses I've added to my router don't seem to help. I blame my router for that.
The reason I needed to add a DNS sever was to find a HOWTO to pmount my addition HDD that couldn't be pmounted. After I found a HOWTO it suggested I add it to pmount.allow. I couldn't it's read only and owned by root.
I tried to install automatix and in the installation instructions it asks to you add a line to /etc/apt/source.list it's read only grrrr. 

Also tonight I was going to have a look through Sypnatic Package Manager but when I clicked to open it after a few seconds of HDD action nothing happens and the same with networking as well but I guess resolve.conf has decided to save my DNS addresses because I'm able to view this site.

I know it sounds like I'm complaining but I'm just a bit frustrated, after a few searches through these forums I can't seem to find anything that helps me with my read only problem, so I decided to post my own thread.

tia

---

### Post by roostishaw on 2006-08-05
```
sudo gedit /etc/resolve.conf
```
...should let you save your changes.

---

