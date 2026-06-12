---
title: "Firefox not loading after update"
date: 2009-05-29
forum: General Help
---

### Post by mrskimmyl on 2009-05-29
I just, literally, a few hours ago, installed Ubuntu on an older, "spare" laptop of mine. Afterwards, I got it up & running just fine & was thrilled with it. I was prompted to download some updates, I went ahead & did that & shut down. Now when I try to open up Firefox it won't load. After clicking on it, from both the panel & the Applications menu, I get a "Starting Firefox Web Browser" on the bottom panel, but then it disappears & Firefox never starts. I have no idea of where to go or what to do from here; I've never used a Linux OS before, so I'm really at a loss. Any help would be immensely appreciated. Thanks!

---

### Post by trench.me on 2009-05-29
Sounds like a package might have broke. Open a terminal (Applications > Accessories > Terminal) and paste the following:

```
sudo apt-get -f install
```

This is an attempt for apt-get to repair anything broken.

---

### Post by trench.me on 2009-05-29
Don't worry about my usage of the word "broken". In linux, especially Ubuntu, and thanks to the awesome community surrounding it, very few things are ever truly "broken". It just means that there was possibly a snafu during the update you ran. 

Also, welcome to Ubuntu. :) 

You've made one of the best computing decisions of your life.

And you're about to fall in love with having full control over your entire OS.

---

### Post by mrskimmyl on 2009-05-29
> **trench.me said:**
> Sounds like a package might have broke. Open a terminal (Applications > Accessories > Terminal) and paste the following:

```
sudo apt-get -f install
```This is an attempt for apt-get to repair anything broken.

Thanks for the quick response! When I tried your suggestion I got back the following:

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

I went ahead & input what is said "sudo dpkg --configure -a", it did a bunch of, um, gobbly gook (yes, I'm sure that's the technical term for it), & fixed the problem! 

Thank you so much for your help & for the warm welcome! I've just started reading the Ubuntu Pocket Guide to try & familiarize myself with all of this, so hopefully, if I encounter another problem, I won't be so lost.

---

