---
title: "Best method to reduce unused applications from LXDE in LXLE 18.04 LTS?"
date: 2024-11-22
forum: Desktop Environments
---

### Post by vector3 on 2024-11-22
I'm currently working on my 32-bit netbooks and just completed the update of lxle. Before migrating to another 32-bit OS I would like to see if I can slim this down and make it more efficient. I prefer to take this task as an initial step for the end goal as well as the learning exercise. At the end of this trail I suspect one of my netbooks will wear Bunsen.

For example, I never need games on any computer. How might I learn what else is in this package and the dependencies tied to these applications?

---

### Post by grahammechanical on 2024-11-22
I am unfamiliar with the LXLE distribution of Linux. The same applies to the LXDE desktop environment. How did you update lxle? Did you use a terminal? Does it have a software center that will install and remove applications? What is wrong with using

```
sudo apt remove <packagename>
```

and 

```
sudo apt purge <packagename>
```

I have discovered that the LXLE web site is temporarily unavailable. I have seen reports that LXLE is no longer being maintained. I wonder what software repositories LXLE uses. Debian perhaps.

Regards

---

### Post by vector3 on 2024-11-23
Yes, LXLE is no longer an option. I suspect Focal is the final update and you can still download this if you desire. I chose to use the internal Sakura terminal to update it in view of a broken dependency that was identified when I first attempted to use the GUI to update it. My issue regarding packages is that I do not know what the packages are and what they consist of.

---

