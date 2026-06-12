---
title: "Can't create ISO-8859-15"
date: 2009-05-28
forum: General Help
---

### Post by ajb2 on 2009-05-28
Hi, everyone,

A month or so ago, I installed Ubuntu via Wubi.  I prefer to set LANG to en_US.ISO-8859-15, and I found that I had to do this to get it to work:

   locale-gen en_US.ISO-8859-15

It worked.  Later, though, we decided to switch and make our system a Ubuntu-only system, so I installed Ubuntu 9.04 from a CD and wiped Vista off the system [pause while waiting for everyone to stop cheering]; but I can't figure out how to get the above locale to work.  When I use the above locale-gen command, it just exits without displaying anything (same if I use 8859-1), and it doesn't work.  I'm guessing there are some files missing, but I don't know what they are or where to get them.

Thanks for any help you can provide.

---

