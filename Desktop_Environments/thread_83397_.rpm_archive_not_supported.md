---
title: ".rpm archive not supported"
date: 2005-10-28
forum: Desktop Environments
---

### Post by drguitarum2005 on 2005-10-28
When I try to run a .rpm by double clicking it on my desktop, archive manager opens but then errors and says "archive not supported". what can I do to correct this?

---

### Post by Kyral on 2005-10-28
Its right. You cannot use RPMs on Ubuntu. At least as they are.

First make SURE you cannot get whatever it is through Apt or even as a .deb

If you cannot then you have to use Alien to convert it.

```
sudo alien <RPM>
```

will attempt to turn it into a Debian archive, but its not 100%. If its successful, then install the deb with

```
sudo dpkg -i <nameofdeb>
```

---

### Post by dto on 2005-10-28
It should also probably be noted that the RPM ([Redhat Package Manager](http://www.redhat.com/docs/manuals/linux/RHL-7.2-Manual/custom-guide/ch-rpm.html)) format was developed by Redhat and is intended for Redhat-based systems (Fedora, Mandriva, etc.). 

Since Ubuntu is based on Debian, it uses the .deb package format.

---

### Post by Kyral on 2005-10-28
Yah...I should have explained that....sorry I'm slipping today...

---

