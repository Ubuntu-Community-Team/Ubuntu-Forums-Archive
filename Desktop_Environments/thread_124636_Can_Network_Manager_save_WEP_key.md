---
title: "Can Network Manager save WEP key?"
date: 2006-02-01
forum: Desktop Environments
---

### Post by Super King on 2006-02-01
I have Network Manager running on startup, and when it attempts to connect to my WEP-encrypted network at home, it will always ask me to enter my key, or save a password in the key ring. Naturally, this is a pain in the neck. Is there any way to enter the WEP key once and have Network manager recognize it forever?

---

### Post by jannol on 2006-02-01
isn't it saved by default? on my old dell latitude it remember it when rebooting. I haven't tried a long shutdown as eg 24 hours.

---

### Post by soulestream on 2006-02-01
I had to manually add my key to /etc/network/interfaces to get it to stay put.

soule

---

### Post by Super King on 2006-02-01
Hmm, mine already seems to be in my interfaces files.

> wireless-key s:*WEP KEY*

---

### Post by seanieb on 2008-04-13
I have been having the same issue and I was hoping that every time I update that it would be solved. 

Where do I file a bug report?

---

### Post by bdstein on 2008-04-13
I say don't use NM, I set mine up manually and never had a problem with rebooting and having to enter it again.

There is a great how to on this thread:
[[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)]("http://ubuntuforums.org/showthread.php?t=571188")

---

