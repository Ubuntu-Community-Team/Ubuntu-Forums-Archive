---
title: "can I keep all .deb files after each update?"
date: 2006-07-17
forum: Desktop Environments
---

### Post by pmark on 2006-07-17
I want to keep the .deb files for every update I am performing.

I am a new user and I am trying all kinds of stuff so I expect "disaster" to appeach in a while. I have a humble DSL line, and the updates take quite some time. It's faster to have the big volume of them in a CD-RW (and updates every once in a while) than download them from scratch.

I know that Linux has nothing to do with the mess of Windows, it's just that I want to feel free to tweak stuff.

How can I keep the .deb files?

---

### Post by aysiu on 2006-07-17
/var/cache/apt/archives is where they're kept.

If you want to make a CD repository:
[http://help.ubuntu.com/community/AptMoveHowto](http://help.ubuntu.com/community/AptMoveHowto)

I would do this instead, though, might save you some trouble:
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by ardchoille on 2006-07-17
> **aysiu said:**
> /var/cache/apt/archives is where they're kept.

If you want to make a CD repository:
[http://help.ubuntu.com/community/AptMoveHowto](http://help.ubuntu.com/community/AptMoveHowto)

I would do this instead, though, might save you some trouble:
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

Hey, aysiu, thank you for those links. They are very helpful :)

---

### Post by pmark on 2006-07-18
Thank you.

Initially, I was thinking some more simple, like burning the .deb packages into a CD, and then re-installing with apt-get.

---

