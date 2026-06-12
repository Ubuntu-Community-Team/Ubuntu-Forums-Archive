---
title: "Unknown Nvidia driver error"
date: 2009-04-23
forum: General Help
---

### Post by Sedatcom4 on 2009-04-23
I just installed ubuntu 8.10 today and did a package update before anything. After the update I tried to simply go to the hardware driver app and when I clicked on the recommended driver for my card (version 180), it gave me this message:

SystemError: E:Unable to correct problems, you have held broken packages.


I don't know what broken packages I have or anything. I am at a loss for what to do. Please help. My card is Nvidia 7600 GT if that helps at all.

I already used the filter in synaptic and nothing shows up. I also tried```
sudo apt-get install -f 
``` to no avail. These are the results: ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by CatKiller on 2009-04-23
Packages that are held (locked from future upgrades) should show up in the Status tree in Synaptic as "Pinned."

---

### Post by Sedatcom4 on 2009-04-23
So, how do I know which ones are to be upgraded?

---

### Post by Sedatcom4 on 2009-04-23
Nevermind. I figured out what it was. Thanks for the help. :)

---

