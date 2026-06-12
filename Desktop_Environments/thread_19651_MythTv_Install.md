---
title: "MythTv Install"
date: 2005-03-13
forum: Desktop Environments
---

### Post by kepsux on 2005-03-13
Edit: Can a mod move this to the correct "other software" section for me? My bad!

Heh, two questions from an experienced Linux user but new to Ubuntu/Debain... What apt-get install variable do you use to install mythtv? I have found documentation stating the package name is in fact mythtv, but it shoots me one of these guys : 

```
E: Couldn't find package mythtv
```

I tried seaching for the word myth is what I assume is the Package Lists with the command 

```
apt-cache search myth
```

but it dosen't return any hits. So onto my second question...how does one go about determining what the name of a package is to install it? I know there are some fancy graphical utilities that spilt them up, whats the best one to start with?

---

### Post by IceAxe18 on 2005-03-13
Im not sure if this will help you but here is a link that may help you out.

[MythTV](http://dijkstra.csh.rit.edu/~mdz/debian/dists/unstable/mythtv/)

---

### Post by kepsux on 2005-03-13
Yea, I checked that out and added the page's suggested link into my sources.list file, but now there are a ton of dependency failures during the install....and yes I tried using aptitude as reccomended in millions of posts. Still lost.... if anyone has any other ideas hit it up. Thanks!

---

### Post by schaez on 2005-03-13
You should be able to find MythTv packages in multiverse repository.

---

