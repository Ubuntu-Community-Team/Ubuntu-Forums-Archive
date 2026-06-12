---
title: "avant-window-navigator and public keys"
date: 2009-01-21
forum: General Help
---

### Post by Knacker on 2009-01-21
Hi, 
I'm suddenly getting an error when i apt-get update. The problem is in the [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy repository. 

Tried removing and re-adding the repository and get this error: 

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5

Can't figure out how/where to get the key it's asking for. Please help. 
Thanks!

---

### Post by Greyhound- on 2009-01-22
I seem to be experiencing the exact same issue as the OP.

---

### Post by sakthi on 2009-01-22
I too get this error. :(

---

### Post by SuperBo on 2009-01-22
> Important: Over the next few weeks, Launchpad is generating keys for each PPA. While this is happening, one of two things will happen when you install software from a PPA.

[https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories](https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories)

---

### Post by kinggo on 2009-01-23
this is how I solved it........
[http://gentoo-blog.de/](http://gentoo-blog.de/)

---

### Post by Knacker on 2009-01-23
> **kinggo said:**
> this is how I solved it........
[http://gentoo-blog.de/](http://gentoo-blog.de/)


worked for me too. thanks!

---

### Post by styyle14 on 2009-01-23
In case the site changes its main page, which I feel it most likely will within the next month, here are the steps it lists to solve the problem:

In the terminal enter:
```

gpg --keyserver subkeys.pgp.net --recv 7D2C7A23BF810CD5

```
then enter:
```

gpg --export --armor 7D2C7A23BF810CD5 | sudo apt-key add -

```

Hope this helps!

---

### Post by shripad_nayak on 2009-02-20
> **styyle14 said:**
> In case the site changes its main page, which I feel it most likely will within the next month, here are the steps it lists to solve the problem:

In the terminal enter:
```

gpg --keyserver subkeys.pgp.net --recv 7D2C7A23BF810CD5

```
then enter:
```

gpg --export --armor 7D2C7A23BF810CD5 | sudo apt-key add -

```

Hope this helps!


This fixed my problem... Thanks

---

### Post by forger on 2009-02-22
[thread=1056099]**Update your Launchpad PPA repositories and apt keys**[/thread]

---

### Post by titico on 2010-03-25
Hey guys,
I have the same issue here, but the gpg key update is not workin for me.
I get this message "gpg: keyserver receive failed: keyserver error"

Any idea on whats happenning? I just executed the two commandos from the gentos blog.

---

