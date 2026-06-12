---
title: "How do you install Java onto ubuntu?"
date: 2009-06-04
forum: General Help
---

### Post by Word Life on 2009-06-04
Well, I need to install JDK and JRE onto my computer. I have no idea how to do it. Any ideas?

---

### Post by oldos2er on 2009-06-04
```
sudo apt-get update && sudo apt-get install sun-java6-jre sun-java6-jdk
```

---

### Post by Word Life on 2009-06-04
This is what I get.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gsfonts-x11 sun-java6-bin
Suggested packages:
  sun-java6-demo sun-java6-doc sun-java6-source sun-java6-plugin
  ia32-sun-java6-plugin sun-java6-fonts
The following NEW packages will be installed:
  gsfonts-x11 sun-java6-jdk
The following packages will be upgraded:
  sun-java6-bin sun-java6-jre
2 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/52.2MB of archives.
After this operation, 156MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

---

### Post by oldos2er on 2009-06-04
That's normal. Hit "y" to continue with the install. When the EULA comes up, hit 'Tab' to highlight ok, then Enter.

---

