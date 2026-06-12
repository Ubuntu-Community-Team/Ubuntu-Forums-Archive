---
title: "about a driver for wifi (trying to use svn)"
date: 2009-02-23
forum: General Help
---

### Post by eagleye on 2009-02-23
I have the intrepid 8.10 dist and  2.6.27-7-generic core.
I tried to "make" the madwifi-0.9.4  but it gave me the common error the 'implicit declaration of function '__skb_append' so I typed " svn co [http://svn.madwifi-project.org/madwifi/branches/madwifi-0.9.4](http://svn.madwifi-project.org/madwifi/branches/madwifi-0.9.4) madwifi-branch-0.9.4" (as I was told to by "http://madwifi-project.org/ticket/2189" but than I had the problem everybody on that page had:"format not a string literal and no format arguments" and now after seeing that I did'nt understand exactly what to do here.
can anyone help me?

---

### Post by ddrichardson on 2009-02-24
I got it to build OK
```
svn co http://svn.madwifi-project.org/madwifi/branches/madwifi-0.9.4
```
I built it under Arch which is running 2.6.28, gcc 4.3.3-1 and SVN 1.5.5-1.

---

