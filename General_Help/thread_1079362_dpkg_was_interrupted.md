---
title: "dpkg was interrupted"
date: 2009-02-24
forum: General Help
---

### Post by colonsay on 2009-02-24
new to linux, dvd would not play, pasted code in terminal, did something else, now when I go into synapic packet manager I get 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

what do I do

---

### Post by sisco311 on 2009-02-24
run:
```
sudo dpkg --configure -a
```in  a terminal.

---

### Post by fooman on 2009-02-24
what sisco said for the dpkg problem.  follow it up with this:

```
sudo apt-get update
```

see if any errors pop up.

for dvd playback...may want to take a look here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by colonsay on 2009-02-24
sudo dpkg --configure -a .....code solved the problem, thank you all ):P

---

