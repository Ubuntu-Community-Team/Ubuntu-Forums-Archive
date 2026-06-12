---
title: "Uninstalling software not got through Synaptic"
date: 2009-02-09
forum: General Help
---

### Post by frankwakeman on 2009-02-09
I got a bit of advice that didn't work from the Swiftfox forum.  I'd installed Swiftfox - if you didn't know, a version of Firefox that comes in different forms for different processors - but found it seemed ot muck up my fonts.  I was adviced to type something in terminal that didn't work, something like sudo apt-get remove Swiftfox (whatever was suggested is what I typed, if I've got that slightly wrong here).

The program remained after this, however.  I even agreed to have some other things removed as prompted in the terminal screen, files which I assumed were related to Swiftfox.

Thanks for any input.

---

### Post by zvacet on 2009-02-09
```
sudo dpkg --remove --force-remove-reinstreq package_name
```

---

