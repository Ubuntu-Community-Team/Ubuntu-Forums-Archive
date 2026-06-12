---
title: "How do I add Xubuntu to Ubuntu?"
date: 2006-10-06
forum: Desktop Environments
---

### Post by boredguy on 2006-10-06
Is it possible to upgrade from ubuntu to xbuntu without having to download and install more CDs? I'm using Ubuntu 6.06 Daper Drake [EMAIL="dane.45@gmail.com"]dane.45@gmail.com[/EMAIL]

---

### Post by Beernut on 2006-10-06
You can open a terminal and type the following.

```
sudo apt-get update
sudo apt-get xubuntu-desktop
```

log out then click on sessions and choose xubuntu and log in.

---

### Post by confusimo on 2006-10-15
I thought I'd give that a try too.  The first line worked great.  But the second line said:

E: Invalid operation xubuntu-desktop

Do I have to download xubuntu first?

Thanks,
Confusimo

---

### Post by aysiu on 2006-10-15
Please don't use *apt-get*. Use *aptitude*--will make it easier to remove later, should you wish to do so: ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
```

---

### Post by confusimo on 2006-10-15
Never mind I found it in synaptic.

---

### Post by aysiu on 2006-10-15
> **confusimo said:**
> Never mind I found it in synaptic.
Synaptic's the same deal as *apt-get*. If you install it through Synaptic, it'll be difficult to remove later.

If you know you don't ever want to remove it, that's cool, though.

---

### Post by Peepsalot on 2006-10-15
> **aysiu said:**
> Synaptic's the same deal as *apt-get*. If you install it through Synaptic, it'll be difficult to remove later.

If you know you don't ever want to remove it, that's cool, though.
I've heard this mentioned before.
If synaptic is just a front end for apt-get, wouldn't it be fairly trivial for the developers to swap it out and make it a front end for aptitude instead?  Are there specific reasons for not doing this?

---

### Post by aysiu on 2006-10-15
I think you should read [this thread](http://ubuntuforums.org/showthread.php?p=1292179#post1292179).

---

### Post by confusimo on 2006-10-16
I don't keep too many important things on the drive so I can reinstall anytime I feel like.  No bigee.  So I don't mind.  Even if its not permanent its no bigee.  And I always have a backup drive anyway.

Andyway I thing this may even be better than ubuntu with gnome.  At leasst looks wise.

But 1 thing.  Where did the trash disappear to?

Thanks,
Confusimo

---

### Post by aysiu on 2006-10-16
There is no trash in Xubuntu... at least not in Dapper.

Edgy will be released in a few weeks--that'll have a trash for Xubuntu.

---

### Post by confusimo on 2006-10-16
If there's no trash then where do the deleted files go and what if you accidently deleted something and want it back.

Thanks,
Confusimo

---

### Post by Peepsalot on 2006-10-16
You just try to be more careful?

---

