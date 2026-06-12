---
title: "Problem with not defined colors"
date: 2006-05-10
forum: Desktop Environments
---

### Post by borix on 2006-05-10
When i want to run some program like xterm, or early firefox(both from terminal), I get this two errors:
Warning: Color name "#e9e5e8 " is not defined
Warning: Color name "#000000 " is not defined

I search a lot, but i don´t find anything.
And still I know that it is not the problem with rgb.txt because I solved this problem, yet.
Can anyone help me?

---

### Post by borix on 2006-05-14
I continued with search and finaly today I found it. I had to downgrade xrdb to version 0.99.1-1(from the following link: [http://tank.cns.utoronto.ca/linux/ubuntu/pool/main/x/xrdb/xrdb_0.99.1-1_i386.deb](http://tank.cns.utoronto.ca/linux/ubuntu/pool/main/x/xrdb/xrdb_0.99.1-1_i386.deb) ) and add line xrdb-use-cpp to /etc/X11/Xsession.options.

---

