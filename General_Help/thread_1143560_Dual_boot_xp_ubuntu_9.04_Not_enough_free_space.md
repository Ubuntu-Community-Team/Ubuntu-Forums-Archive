---
title: "Dual boot xp ubuntu 9.04: Not enough free space"
date: 2009-04-30
forum: General Help
---

### Post by perryg84 on 2009-04-30
Hello, 

I installed the latest 64bit release.

The installer gave me the option to install side by side with windows xp. The installation was successful but now when I try to perform an update etc I receive warning message that there is not enough free space. 

I checked the system admin options but there is no partition tool installed.

I am confused. What can I do to allocate more space?????

Any help is greatly appreciated!

---

### Post by raequin on 2009-05-06
Have you gotten any help yet?

I have just encountered the same thing today; looking for a solution.

---

### Post by Legace on 2009-05-06
Boot into the LiveCD environment.
Open Terminal in Applications.
Type in the following and press Enter:
```
sudo gparted
```


Now you will be able to edit the partitions :)

EDIT: You might find some help here: [http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by raequin on 2009-05-06
Cool, thanks.  I will do that when I get home.

Do you know what the rationale is for having the "side by side" install make a partition so small that you can't add updates?

---

### Post by silentknyght on 2009-05-06
> **raequin said:**
> Cool, thanks.  I will do that when I get home.

Do you know what the rationale is for having the "side by side" install make a partition so small that you can't add updates?

It needs to start somewhere? :)

---

