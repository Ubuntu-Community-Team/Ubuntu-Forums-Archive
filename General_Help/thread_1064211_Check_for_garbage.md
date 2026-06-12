---
title: "Check for garbage"
date: 2009-02-08
forum: General Help
---

### Post by RedSingularity on 2009-02-08
Is there any way i can check for unessisary junk on Ubuntu?  Lets say i uninstall something, is there a way to check if there are any files laying around taking up space?

---

### Post by taurus on 2009-02-08
Autoremove will remove all the unnecessary dependencies on your machine.
 
```
sudo apt-get autoremove
```

---

### Post by RedSingularity on 2009-02-08
If i may ask, do you know how this command knows what to remove?  I am interested to know.

---

### Post by mb_webguy on 2009-02-08
EDIT:  I was thinking of the wrong command.  "sudo apt-get autoremove" removes unused packages.  "sudo deborphan" checks for orphaned packages, which are those which are not applications and which no other packages depend upon.

---

### Post by OrangeCrate on 2009-02-08
HOWTO: Cleaning up all those unnecessary junk files...

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

