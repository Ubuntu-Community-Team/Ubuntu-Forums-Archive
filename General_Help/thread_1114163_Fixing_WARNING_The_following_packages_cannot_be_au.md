---
title: "Fixing: WARNING: The following packages cannot be authenticated!"
date: 2009-04-02
forum: General Help
---

### Post by WitchCraft on 2009-04-02
When you upgrade to a new version of Ubuntu/Debian, then you may see the following message:
```

WARNING: The following packages cannot be authenticated!
  foo bar

```

Searching google doesn't turn up good hits for fixing this, so i provide here the solution to this problem, which is really simple:
```

sudo apt-get remove debian-keyring debian-archive-keyring
sudo apt-get clean
sudo apt-get update
sudo apt-get -y install debian-keyring debian-archive-keyring

```

---

### Post by dev.null on 2010-12-15
Thumbs up.

I've seen a lot of "ack-grep update" recommendations, which of course don't solve this problem

Your advice hands-down fixes it.

Someone should make this a sticky somewhere!

---

### Post by phoenixstew49 on 2012-12-08
I encountered the following error for packages that have previously had no problems,
```
WARNING: The following packages cannot be authenticated!
```The fix given by WitchCraft worked perfectly.
> **WitchCraft said:**
> 
```

sudo apt-get remove debian-keyring debian-archive-keyring
sudo apt-get clean
sudo apt-get update
sudo apt-get -y install debian-keyring debian-archive-keyring

```

---

### Post by Sef on 2012-12-08
Locked. Necromancing.

---

