---
title: "Why not . (dot)"
date: 2008-12-16
forum: General Help
---

### Post by Cool Javelin on 2008-12-16
Why isn't the current directory . in the path?

I notice (For Xubuntu) there are sbin, and bin folders under /usr/local, /usr, and /.

I have noticed this in other distros too.

Is there a reason the current folder (whatever that may be) isn't included in that list?

Thanks, Mark.

---

### Post by taurus on 2008-12-16
/bin, /sbin, /usr/bin, /usr/sbin, & /usr/local/bin are the standard directories where binaries would go/install.  If you want to include the current directory in your path, then you need to edit ~/.bashrc and add these two lines to it.

```
PATH=$PATH:.
export PATH
```

---

### Post by Cool Javelin on 2008-12-16
taurus: 

Thanks, I was going to post that ? on another thread, now I don't have to.

But I was wondering at the philosophy behind the decision not to include the current directory in the first place. I doubt it was an oversight.

Mark.

---

### Post by albinootje on 2008-12-16
> **Cool Javelin said:**
> Why isn't the current directory . in the path?


It is not there for security reasons.

And if you want to add it, you should add it at the *end* of the PATH, like mentioned in another posting.

---

