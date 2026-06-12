---
title: "Reliable Way to get AsRock Dual 939 Online?"
date: 2006-03-07
forum: Desktop Environments
---

### Post by sony102600 on 2006-03-07
Has anyone found a consistent way to get online using the on board ethernet with the AsRock Dual 939 Sata 2 motherboard?  I have this board and have been unable to get ubuntu up and running with a week's worth of reading and trying, am thinking I will probably get a new network card... but was just gunna throw this out there as a last hope.

---

### Post by SlowHorse on 2006-03-07
Does "ifconfig" return any results? What is the output of "lspci"?

I'm guessing that your network card's chipset is a Realtek RTL8201CL. If it is, try the solution posted here:

[http://www.ubuntuforums.org/archive/index.php/t-136525.html](http://www.ubuntuforums.org/archive/index.php/t-136525.html)

There seems to be an entire review dedicated to the motherboard in question at [http://www.phoronix.com/scan.php?page=article&item=355&num=1#](http://www.phoronix.com/scan.php?page=article&item=355&num=1#). I'm assuming it works on one distro or another. Maybe you should try updating the BIOS?

---

