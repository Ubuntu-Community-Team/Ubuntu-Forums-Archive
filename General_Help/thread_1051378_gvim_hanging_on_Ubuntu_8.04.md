---
title: "gvim hanging on Ubuntu 8.04"
date: 2009-01-26
forum: General Help
---

### Post by hasana on 2009-01-26
Hello,
I have recently hit a problem where gvim seems to hang when I start it up. If I press ctrl-c then an empty gvim window does appear. I ran gvim in strace and it seems that gvim was stuck in:

connect(15, {sa_family=AF_FILE, path="/tmp/.esd-1000/socket"}

So, I killed gvim and removed the file /tmp/.esd-1000/socket and now gvim seems to be working fine now. I have no idea why it stopped working.

Just thought I'd post this in case someone came across a similar problem (or I hit it again and forgot what I did ;))
adil

---

