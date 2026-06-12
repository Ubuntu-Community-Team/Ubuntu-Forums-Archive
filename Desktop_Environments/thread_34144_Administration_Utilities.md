---
title: "Administration Utilities"
date: 2005-05-13
forum: Desktop Environments
---

### Post by ubunME on 2005-05-13
I have just fininshed my installation of Ubuntu, but I cannot access any of the utilities under System -> Administration.  I was trying to access the Network Configuration settings, but the busy cursor/wheel just spins and then returns to the arrow.  I saw a different thread that was somewhat similar and it suggested using 

$ sudo gdmsetup 

for the logon screen setup, but I am unsure of where to find out how to access the other utilities.

---

### Post by az on 2005-05-13
Very strange.  Perhaps some of the installation did not happen.

From the command line (open a terminal or do CTRL-ALT-F1) and do
sudo apt-get -f install

---

### Post by ubunME on 2005-05-13
I ran the sudo apt-get -f install command and had a warning returned "unable to look up public/pickup: No such file or directory."  After that it read the package list and built the dependency tree.  After that is returned "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

---

