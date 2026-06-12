---
title: "installing XQF with synaptic"
date: 2005-06-11
forum: Gaming &amp; Leisure
---

### Post by Eazy© on 2005-06-11
Hi!
I get this error when I try to install XQF with synaptic (XQF depends in qstat):

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/q/qstat/qstat_2.7-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/q/qstat/qstat_2.7-1_i386.deb)
  MD5-kontrollsumma stämmer inte (= MD5- does not match. For the non swedish dudes ;) )

Is this somthing that is wrong with my linux or is it the package at the server that are broken or something (I can install other pakages).

I'm kind of a newbie on linux and dont really know what the MD5-thingie does or what its fore. I got an idéa what it is, but I dont dare to tell becaus you would laugh your asses of ;)

---

### Post by Xian on 2005-06-11
The us.archive mirror is having issues at the momment. 
Try replacing them in your sources.list file with the one below.
Remove any unwanted repos before updating. 

```
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
```

---

### Post by Eazy© on 2005-06-11
Thanx! That did the trick.

---

