---
title: "Apptitude Install Failed"
date: 2006-08-04
forum: Desktop Environments
---

### Post by sign_of_enigma on 2006-08-04
I was trying to install KDE support in Ubuntu 6.06 (Dapper Drake)..But When I typed in the following Command On the shell of administrator...
sudo apt-get install desktop-kubuntu

---- 
I got the following Error..

Reading Package List ....Done
Building Dependency Tree ....Done
E: Couldn't Find package desktop-kubuntu

please help me ... where is problem and what I should do.

---

### Post by MerZo on 2006-08-04
> **sign_of_enigma said:**
> I was trying to install KDE support in Ubuntu 6.06 (Dapper Drake)..But When I typed in the following Command On the shell of administrator...
sudo apt-get install desktop-kubuntu

---- 
I got the following Error..

Reading Package List ....Done
Building Dependency Tree ....Done
E: Couldn't Find package desktop-kubuntu

please help me ... where is problem and what I should do.

Try the command sudo aptitude install kubuntu-desktop

The problem is that the package is named kubuntu-desktop, but using aptitude instead of apt-get will make it easier for you to unistall the software later on if you want to.

---

