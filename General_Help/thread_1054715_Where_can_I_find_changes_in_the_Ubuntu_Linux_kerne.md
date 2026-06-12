---
title: "Where can I find changes in the Ubuntu Linux kernel?"
date: 2009-01-30
forum: General Help
---

### Post by altonbr on 2009-01-30
I have Ubuntu 8.10 installed and with it, I have kernel 2.6.27-11. When I did a fresh install, I had 2.6.27-7 and then updated to -11. I had no sound in -11 until a recent update.

I'm curious at to where I can find the changes that occurred in the Linux kernel within Ubuntu.

The usual website I check, Launchpad.net, gives me no hope in finding the linux-image packages and encompassing changes.

Can someone point me in the right direction?

Failed searches:
[https://launchpad.net/ubuntu/+search?text=2.6.27](https://launchpad.net/ubuntu/+search?text=2.6.27)
[https://launchpad.net/ubuntu/+search?text=linux-image](https://launchpad.net/ubuntu/+search?text=linux-image)
[https://launchpad.net/ubuntu/+search?text=2.6.27-11](https://launchpad.net/ubuntu/+search?text=2.6.27-11)
[https://launchpad.net/ubuntu/+search?text=linux+2.6.27](https://launchpad.net/ubuntu/+search?text=linux+2.6.27)

---

### Post by altonbr on 2009-01-30
My apologizes... it's not the same as the package name installed, but pretty self explanatory: [https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux)

---

### Post by scouser73 on 2009-01-30
In Terminal paste > uname -r

---

### Post by sdennie on 2009-01-30
Have a look at the file:

```

/usr/share/doc/linux-image-`uname -r`/changelog.Debian.gz

```

If your editor doesn't know how to automatically gunzip things, you may need to gunzip the file first.

---

