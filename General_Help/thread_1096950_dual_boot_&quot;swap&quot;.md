---
title: "dual boot &quot;swap&quot;"
date: 2009-03-15
forum: General Help
---

### Post by dark of angel on 2009-03-15
salam,i still new in ubuntu and i wannna know in doing dual boot installation and after the shoosing manual setting whats the "swap",sorry because i mjust in the first step on learning

---

### Post by oldos2er on 2009-03-15
The swap partition serves as virtual memory. See [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by JDorfler on 2009-03-15
"Swap" is the Virtual Memory for Linux.  Unlike Win, Linux uses a set swap partition instead of fragmenting all your data with the same partition you would store your OS, Applications, or Data.  In order create your swap partition, go to system>admin>partition editor (Gparted) and create a new swap partition using the Ubuntu LiveCD.  I would go with swap=ram*2 if your ram is under 2Gb.  However, if your ram is over 2Gb, I would go with swap=ram*1.5 so you know you can use the hibernate function.  Also, make sure you label your Linux partition "/".  This is where you want to install Ubuntu.  It's also a great idea to create another partition named "/home" so if you decide to trade up distros, you won't lose all your personal data.

---

