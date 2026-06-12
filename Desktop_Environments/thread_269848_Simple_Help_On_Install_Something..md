---
title: "Simple Help On Install Something."
date: 2006-10-02
forum: Desktop Environments
---

### Post by mikeqq on 2006-10-02
Hey, I just got ubuntu today and I am very happy.
I want to start off by installing a couple of programs.
I downloaded FrostWire, its in ZIP format.
How do I install it? 
Can someone please explain to me

Thanks :)

---

### Post by aysiu on 2006-10-02
Step 1. Delete the .tar.gz you downloaded.

Step 2. Paste these commands into the terminal: ```
wget -c http://mirror1.peercommons.net/frostwire/4.10.9/FrostWire-4.10.9-2.i586.deb
sudo dpkg -i FrostWire-4.10.9-2.i586.deb
rm FrostWire-4.10.9-2.i586.deb
```

---

