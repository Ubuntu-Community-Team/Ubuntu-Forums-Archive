---
title: "How do I install Java on firefox?"
date: 2009-01-29
forum: General Help
---

### Post by mahela007 on 2009-01-29
How do I install Java on firefox? Anything special I have to do because it's on linux?

---

### Post by rwstoner on 2009-01-29
Installing Java is pretty simple if you use the apt-get command.

Run this in a terminal:

**sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin**

You may need to do an 'apt-get update' before hand and be sure to restart Firefox before testing.

Firefox itself also has a nice plug in manager that should prompt you to install the "IcedTea Web Broswer Plugin" automatically when you try to load Java applets.  Once that installs just restart Firefox and it should work fine.

---

