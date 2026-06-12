---
title: "How to Hide Drives from Ubuntu?"
date: 2008-07-10
forum: Desktop Environments
---

### Post by capatt on 2008-07-10
Hello
      I have a triple-boot system (XP, Vista, Ubuntu) with multiple hard drives.  Two of the hard drives are actually configured as RAID1 in Windows, but Ubuntu sees these as two separate drives, of course.  I'd like to hide these altogether from ubuntu so nothing accidental can happen to the data on those and muck up the mirroring.  Plus, it just clutters up my file managers, etc.
      Is there a setting within Ubuntu that can be used to permanently hide other hard drives?

Thank you!

---

### Post by sayakb on 2008-07-10
You can remove their entries from fstab to prevent them from automounting on boot. Keeping them unmounted will not do any harm.
At a terminal:
```
sudo gedit /etc/fstab
```And add # in front of the drives you dont want to mount. If you want us to do it, post the output of the commands:
```
cat /etc/fstab
```

---

### Post by capatt on 2008-07-15
Hello
      I solved the issue by downloading a package called Storage Manager which is a GUI allowing one to set all those options.

Thanks for your help.

---

