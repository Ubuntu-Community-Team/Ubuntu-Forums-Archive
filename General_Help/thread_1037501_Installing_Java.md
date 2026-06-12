---
title: "Installing Java"
date: 2009-01-11
forum: General Help
---

### Post by oldtraveler on 2009-01-11
I need to install the latest java in order to play Pogo games.  Following their instructions leads me into no mans land. I have downloaded and saved to usr/java folder this file (jre-6u11-linux-i586.bin).  How can I get it installed?

---

### Post by taurus on 2009-01-11
You can install java from the repos.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
When you get to the java license screen, hit the Tab key to highlight the <OK> and Return to accept it.  Once it's installed, you have to restart firefox.

---

### Post by oldtraveler on 2009-01-11
I forgot about Synaptic.  It looks like that solved the problem.

---

