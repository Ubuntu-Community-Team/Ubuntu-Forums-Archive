---
title: "Java Help"
date: 2009-01-09
forum: General Help
---

### Post by ShawnMichael on 2009-01-09
I'm trying to install Java so I could play games on pogo.  But the instructions is so vague and difficult to follow or understand.  I'm a first time Linux user.  I am using the latest version of Ubuntu.  I went to java.com and downloaded rpm and self extracting files, but none of their instructions make it easier for me to understand.  Can anyone help?

---

### Post by taurus on 2009-01-09
Install the version from the repos.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
You have to hit the Tab key to highlight the <OK> at the licensing screen and then Return to accept it.  You need to restart firefox after you have installed java on your machine.

---

### Post by ShawnMichael on 2009-01-10
thanks :) it worked

---

### Post by tuxxy on 2009-01-10
Java is included with the ubuntu-restricted-extras package along with flash, codecs etc this should be installed on any fresh system.

---

