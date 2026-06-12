---
title: "How to access files accessible only for root?"
date: 2009-01-11
forum: General Help
---

### Post by MarkenK on 2009-01-11
Hello!
I have a fan and wireless switch problem on FJ amilo 1310

I found a guide to help me out of it. I have to drag and copy a file to /etc/initframs-tools, but it is accessible only for root.

What should i  do?

The guide is at: [https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuAmiloL1310G](https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuAmiloL1310G)

Thanks in advance!

---

### Post by oldos2er on 2009-01-11
Open a terminal and type "gksu nautilus". This will give you admin privileges to move files where they need to be. Be careful!

---

### Post by MarkenK on 2009-01-11
It didn't work. Still can't lift the file, where i need it, neither change permissions.

---

### Post by MarkenK on 2009-01-11
ah, found an answer

the correct line would be gksu thuram

---

