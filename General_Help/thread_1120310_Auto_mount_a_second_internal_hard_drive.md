---
title: "Auto mount a second internal hard drive"
date: 2009-04-08
forum: General Help
---

### Post by hufferd on 2009-04-08
I have a second internal The icon for it does not always show on the desk top after a reboot -- is it not mounted at the time....?? I want to make sure that it is mounted all the time after a log in.  What can I do to make sure this happens or is it automatic? 

D

---

### Post by Tim Sharitt on 2009-04-08
Is the second hard drive listed in /etc/fstab?

If it is not and you would like to add it to be mounted at boot, I would suggest looking at bodhi.zazen's fstab how to: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by hufferd on 2009-04-08
> **Tim Sharitt said:**
> Is the second hard drive listed in /etc/fstab?

If it is not and you would like to add it to be mounted at boot, I would suggest looking at bodhi.zazen's fstab how to: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Ok thanks will take a look

---

### Post by dcstar on 2009-04-09
> **hufferd said:**
> I have a second internal The icon for it does not always show on the desk top after a reboot -- is it not mounted at the time....?? I want to make sure that it is mounted all the time after a log in.  What can I do to make sure this happens or is it automatic? 

D

Install the **pysdm** package.

---

