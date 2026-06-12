---
title: "GPG error during apt-get update"
date: 2009-04-07
forum: General Help
---

### Post by Dj Dutchman on 2009-04-07
Hi, this problem actually started a while ago when I suddenly couldn't update a few of my repos but then it decreased to just one. I kept hoping it would just suddenly work but it isn't ;) here is the error I get

> W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) intrepid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems


I'm running Intrepid 64-bit. Anyone know how I can solve this?

---

### Post by kanikilu on 2009-04-07
Try running the following from the terminal:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 437D05B5
sudo apt-get update
```

---

### Post by Dj Dutchman on 2009-04-07
Nope, unfortunately, it didn't work. After I ran it, it said something about some keys changed or something but it still doesn't work. Exactly the same error as well...

---

### Post by kanikilu on 2009-04-07
Hmm, a search brought up this similar thread:

[http://ubuntuforums.org/showpost.php?p=6103997](http://ubuntuforums.org/showpost.php?p=6103997)

Specifically, try what's suggested in post 6:

[http://ubuntuforums.org/showpost.php?p=6103997&postcount=6](http://ubuntuforums.org/showpost.php?p=6103997&postcount=6)

---

### Post by Dj Dutchman on 2009-04-07
Yet again, it didn't work. I'm trying changing servers to random ones around the world, to see if it's poss a weird combo of my PC a server...

Will let you know how it works...

---

### Post by Dj Dutchman on 2009-04-07
That doesn't seem to be working either...

---

