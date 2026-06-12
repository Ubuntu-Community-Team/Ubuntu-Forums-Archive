---
title: "No mreo room in Ubuntu help!"
date: 2009-02-05
forum: General Help
---

### Post by shorty28898 on 2009-02-05
When i installed ubuntu i was not sure how much room i was going to use.  I have now used it all up, is there anyway to add more?  i have about 50 gb free in windows partition, i want to add like 15 gb to ubuntu.

---

### Post by beno1990 on 2009-02-05
You could always download gparted

```
sudo apt-get install gparted
```

and resize your partitions with that.

However, I tend to not recommend it because it can cause data loss and mess up your partition table and filesystems.

---

### Post by shorty28898 on 2009-02-05
Well i dont want to do anything that isnt rteally recommened..  any other options?

---

### Post by thomasr on 2009-02-05
A good way to do this is to use remastersys to make a live installable cd or dvd of your system, delete the old partition, create a new larger partition and reinstall your system from the lve cd/dvd you created (test  it first)
[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)
[http://en.wikipedia.org/wiki/Remastersys](http://en.wikipedia.org/wiki/Remastersys)
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

---

