---
title: "How to install GCC-4.0.1"
date: 2005-07-27
forum: Desktop Environments
---

### Post by soon82 on 2005-07-27
Basically, I would like to make my Ubuntu as a Samba Server....Once i try to install the SAMBA Package..... It has error regarding the GCC....


After that i try to visit gcc.gnu.org and download the source to my pc....but i don't know how to install this GCC into my PC.....

So i need yours help....

---

### Post by Perfect Storm on 2005-07-27
I'm not an expert on Samba, but are you sure that it need gcc4.0.1? Have you tried Gcc4.0.0 which is avaible through apt-get backports source.


Edit: Just checked the Samba requirements and it says it doesn't need Gcc 4.0.1

---

### Post by soon82 on 2005-07-28
I had type the command apt-get update at the root terminal.... but never see the Gcc4.0.0....

[QUOTE=Artificial Intelligence]I'm not an expert on Samba, but are you sure that it need gcc4.0.1? Have you tried Gcc4.0.0 which is avaible through apt-get backports source.


Edit: Just checked the Samba requirements and it says it doesn't need Gcc 4.0.1[/QUOTE]

---

### Post by tom-ubuntu on 2005-07-28
I am pretty sure that you do not need GCC4 for Samba. Ubuntu is doing the switch to version 4 in Breezy.

---

### Post by Perfect Storm on 2005-08-01
The gcc4.0.0 is availble in the backports. Check the unofficial ubuntu guide on howto setup the repo.


.:=The AI Dude=:.

---

