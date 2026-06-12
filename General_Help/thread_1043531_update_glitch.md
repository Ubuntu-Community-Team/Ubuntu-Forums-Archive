---
title: "update glitch"
date: 2009-01-18
forum: General Help
---

### Post by Bigneil on 2009-01-18
fresh ubuntu install  (heron).  i am experiencing a small glitch with automatic updates.

I'ts probably simple to sort, but it is beyond me:(

i have attached a screenshot of the error message.

Any help will be appreciated

---

### Post by taurus on 2009-01-18
Close the update window manager.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Bigneil on 2009-01-18
great thanks:) the terminal is off whizzing through lines of gobbeldy gook at a rate of naughts.  

I noticed that synaptic was showing the same error and i also could not install a deb package, i hope that they are sorted too.

---

### Post by Bigneil on 2009-01-18
yes it did. all sorted. thankyou very much:)

---

