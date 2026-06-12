---
title: "jgrasp and java 1.5"
date: 2006-01-10
forum: Desktop Environments
---

### Post by jdway on 2006-01-10
I recently installed jgrasp in order to take my CS class and they also informed me that I should be using java 1.5. I followed the wiki on how to install java 1.5 but do I need to uninstall java 1.4 because jgrasp still states uopn startup that it is using version 1.4. If I do need to uninstall version 1.4 how can I get java 1.5 to work in mozilla?

---

### Post by healychan on 2006-01-10
If you install jdk 1.5 as a package. You can edit the primany version of java you use by
```
sudo update-alternatives --config java
```

If you install jdk from bin file, you need to modify the $PATH variable.

The guide in my signature will guide you to do so.

---

