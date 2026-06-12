---
title: "Making Local Repository have more priority"
date: 2009-05-30
forum: General Help
---

### Post by vishy1618 on 2009-05-30
Hi guys, 
I have a local repository of around 2.2 GB consisting of various important apps that I commonly need. I also have enabled the Internet repositories. Now, If I want to download an application, I find that a number of the dependencies are already satisfied by my local repository. Yet, Synaptic still downloads the same version from the Internet. I have a very limited Internet connectivity here and I would prefer that it be a very economical process when downloading applications. I researched around and found something called 'apt-pinning' and making a 'apt-preferences' file if I am correct. But the documentation is very confusing and mostly related to Debian's 'Stable and 'Unstable' Branch (or maybe I was looking at the wrong place). Can anyone please point me in right direction on this issue? Thanks!

---

### Post by geraldvillorente on 2009-05-30
try apt-cacher

---

### Post by vishy1618 on 2009-05-30
Will it detect the local repository I have made( I am installing apt-cacher now). Thanks for the reply.

---

### Post by geraldvillorente on 2009-05-30
No probs

EDIT: Make sure that you will point your proxy to the dir where your packages are located.

---

### Post by vishy1618 on 2009-05-30
Hi, I tried apt-cacher but it is a bit confusing, please help me out...

It makes the directory /var/cache/apt-cacher where it is supposed to cache all the files.
But I already made a local repository in /media/System/VISH/ubuntu-9.04-repo/ and I dont have space for it to copy all that to /var.(I am running a liveUSB)
Can I specify the above path as the place where the cached packages are kept? Or is there some other solution? Thanks for the relplies.

---

### Post by CatKiller on 2009-05-30
> **vishy1618 said:**
> Or is there some other solution?

A symbolic link might work.

---

### Post by vishy1618 on 2009-05-30
Thank you. I love you.
Symbolic link it is, instead of using apt-cacher, i just did a 

ln -s /path/to/local/packages/* /var/cache/apt/archives/

Now it does not download what I already have.
Here's one to Linux's flexibility!

---

### Post by bacardiandwatermelon on 2009-05-30
Would a sym link work? Whoops took too long to write a reply hahaha

---

### Post by vishy1618 on 2009-05-30
> **bacardiandwatermelon said:**
> Would a sym link work?

Works like a charm.

---

### Post by geraldvillorente on 2009-05-30
Nice...I'll try it too

---

