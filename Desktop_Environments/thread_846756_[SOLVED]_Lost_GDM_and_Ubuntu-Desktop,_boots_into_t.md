---
title: "[SOLVED] Lost GDM and Ubuntu-Desktop, boots into terminal"
date: 2008-07-01
forum: Desktop Environments
---

### Post by MrSootentai on 2008-07-01
I accidentally uninstalled gdm and ubuntu-desktop and now my ubuntu only boot into the terminal client.
How can I fix this? Whenever i type in 'apt-get install ubuntu-desktop' it just fails to get any of the packages.
What should I do??

---

### Post by clegends on 2009-05-31
How was this solved? Please don't mark posts as solved until you tell us what you did. Thanks

---

### Post by MrSootentai on 2009-05-31
I don't remember what I did, but most likely just reinstalled because I never received an answer. I just marked as solved because it was already buried so far under.

---

### Post by merlinus on 2009-06-01
```

sudo apt-get install ubuntu-desktop

```

would have done it.

---

### Post by MrSootentai on 2009-06-01
> **merlinus said:**
> ```

sudo apt-get install ubuntu-desktop

```

would have done it.

That hadn't worked. Everytime I did with or without sudo it would say it failed to find the package.

---

### Post by merlinus on 2009-06-01
Interesting....  Did you try

```

sudo apt-get update

```first?  That should have updated the repos, which may be why you got the error.

And 

```

sudo aptitude update
sudo aptitude install ubuntu-desktop

```should work as well.

---

### Post by MrSootentai on 2009-06-01
Mhm, I tried all of that. I even got a clean sources list from a fresh install and it didn't work either. It kept giving the failed to find package for everything. Not just the ubuntu-desktop.
Hence the reason I had reinstalled everything.

---

