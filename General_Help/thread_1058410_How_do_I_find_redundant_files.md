---
title: "How do I find redundant files?"
date: 2009-02-02
forum: General Help
---

### Post by pablo66 on 2009-02-02
I am using Ubuntu 8.04 and have "over backed up" my drives. I have 2 usb drives and after many backups I have found the same files/folders backed up in several locations, so I know there is tons of wasted space. I would like to know if there is an application that is either built into 8.04 or an app that I can load through Synaptic that will find these redundant files. Thanks in advance for any ideas.

---

### Post by SoCalChris on 2009-02-03
fslint is probably what you're looking for. I'm sure there are other programs too, but fslint is the one that I've used in the past.

```
sudo apt-get install fslint
```

[http://www.linux.com/feature/120000](http://www.linux.com/feature/120000)

---

### Post by pablo66 on 2009-02-03
Yes! Thank you. This is exactly what I'm looking for.

---

