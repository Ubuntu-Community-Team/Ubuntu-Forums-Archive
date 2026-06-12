---
title: "Trouble with updates. What does this message mean? (Screenshots included)"
date: 2009-06-11
forum: General Help
---

### Post by Macfunky on 2009-06-11
I turned on my computer to get a caution icon showing up in my notification area. When i click on it, it tries to install updates but i get another message -

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.88.46 80]
Some index files failed to download, they have been ignored, or old ones used instead.

It seems to be preventing me from doing any updates. Anyone know whats wrong and how i can sort it out?? I notice the error message mentions edgy? I have no idea why. Any help would be appreciated. Thanks

Im running Jaunty

---

### Post by drs305 on 2009-06-11
Your sources.list contains at least one reference to edgy. Edgy is no longer supported so the repository doesn't exist.

You can edit your sources.list to remove the 'edgy' references if you are not running edgy.

```
gksudo gedit /etc/apt/sources.list
```

If you are running edgy, you should probably try a newer version of ubuntu. If you insist on retaining edgy, you can change your sources.list to point to the *archived* edgy repositories. Open sources.list as described above and:

If you are using the default repositories, replace all instances of *[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)*  with *[http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)*

---

