---
title: "How do I format my new external hard drive to ext3?"
date: 2009-01-15
forum: General Help
---

### Post by Peter_G on 2009-01-15
Please say in the easiest way possible, n00b here.

---

### Post by Speed Demon on 2009-01-15
> **Peter_G said:**
> Please say in the easiest way possible, n00b here.
Go to Applications -> Acces. -> Terminal and type in 
```
sudo apt-get install gparted
```
Then, when finished, go to System -> Admin. -> Partition Editor and from there you can format your new drive as almost anything you want. :popcorn:
You're Welcome!

---

### Post by Peter_G on 2009-01-15
thanks, but I can't seem to get the format to option, and I'm running it as root :(

---

### Post by T2manner on 2009-01-15
You can't format it until you Unmount it.
Try selecting the Unmount option then go back and see if you can find the Format option.

---

### Post by Peter_G on 2009-01-15
Thank you both!

---

