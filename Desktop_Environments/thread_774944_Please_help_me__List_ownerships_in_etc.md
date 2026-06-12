---
title: "Please help me:  List ownerships in /etc"
date: 2008-04-29
forum: Desktop Environments
---

### Post by Questor21 on 2008-04-29
Don't laugh.  

While in / I accidentally did a:

```
sudo chown -R username:username *
```

:shock:

I stopped it as quickly as I could, but it still got to /boot, /dev, /bin, /etc, and /cdrom.

I tried doing undoing the damage by chowning those back to root:root, but I wasn't surprised when I had problems.  Before everyone left work, I got one of them to send me the directory contents of /dev and with a bit of scripting have restored the correct ownerships of /dev.

I can boot into my desktop again, but when my screen locks I cannot unlock it.  I have read the posts here about 'just passwd yourself' and that does not work.  

I suspect that there are non-root:root objects within /etc.  

**Please just copy/paste the contents of ls -alR /etc, or at least provide me with a list of which files within /etc are non-root:root and what they should be.**

Currently running 8.04.

THANKS.

---

