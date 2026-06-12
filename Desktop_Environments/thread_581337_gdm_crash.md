---
title: "gdm crash"
date: 2007-10-19
forum: Desktop Environments
---

### Post by btt on 2007-10-19
Yesterday I did a fresh install of Gutsy from DVD, and I cannot get gdm to work.  When it runs, the screen flicks to X (successfully - I very briefly see a spinning wait cursor), then immediately bombs to the command line.  Repeats this in the usual fashion until I get the "X keeps crashing" text-mode dialog.

Problem is, I can't locate the source of the error.  /var/gdm/<logs> are all completely empty, no errors in X logs (X works fine using startx / kdm / xdm).  The only clue I can find is in my syslog, where I get the lines:

```
Oct 18 19:17:54 <host> gdm[5341]: WARNING: gdm_cleanup_children: child <PID> crashed of signal 11
Oct 18 19:17:54 <host> gdm[5341]: WARNING: gdm_cleanup_children: Slave crashed, killing its children
```

Where <PID> is a PID - different every time, repeated for every time gdm has tried to start X.  No other surrounding messages of any relevance.

Any ideas anyone?

---

### Post by Xpf on 2007-10-20
I have the identical  problem in my Positivo V42 notebook (Clevo M541SE [http://www.clevo.com.tw/en/products/prodinfo_2.asp?productid=29]("http://www.clevo.com.tw/en/products/prodinfo_2.asp?productid=29").)

I try to instal for Live CD and I verified the CD using the MD5 sun and it is ok.

The Ubuntu Feisty Fawn work fine in this model and the variants to.

I removed my HDD for testing and boot for Live-CD only and the error persist.

Wath are wrong?

Sorry for my poor english it is because I'm Brazilian. :)

---

### Post by ac7ss on 2008-01-14
^BUMP^ 
I am now getting the same thing. it just started in the last few days.

---

