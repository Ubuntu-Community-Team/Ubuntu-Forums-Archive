---
title: "Repository and wifi problems"
date: 2009-02-07
forum: General Help
---

### Post by c-m on 2009-02-07
I have recently install Ubuntu UMPC (I use regular 8.10 on my deslktop) on my Acer Aspire One. 

I have used the regular kernel and sickboys 2.6.28 v4 kernel but I have the following problems:

1) The internal wifi works, but it will not detect my network. It can detect every other network in the street, over 10 of them, but it will not detect or connect to my router even when standing right next to it. I know there is not a problem with the card itself as it works very well in windows all over the house. I tried my USB wifi adapter in the laptop and that works fine too with near 100% signal. I imagine this can only be a driver issue then.

2) I have enabled the multiverse and restricted repositories and updated using sudo apt-get update. But my machine will not find any software when searching. Even packages like Firefox and vlc are not found when searching either via the command line or synaptic.

Does anyone have any ideas on how to fix these problems?

Thanks

---

### Post by mb_webguy on 2009-02-07
For the second problem, try "sudo update-apt-xapian-index".

---

