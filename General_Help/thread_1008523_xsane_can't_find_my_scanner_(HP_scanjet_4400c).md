---
title: "xsane can't find my scanner (HP scanjet 4400c)"
date: 2008-12-11
forum: General Help
---

### Post by Hoobes1 on 2008-12-11
Hi, i just looked around on the internet and found out that in order to make your hp scanjet 4400c to work, you have to install xsane and run it. unfortunately, xsane can't find my device. It says, "No devices available". what can i do to fix this problem?

---

### Post by rbmorse on 2008-12-11
check this page 

[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

about half-way down (manually installing a scanner).

---

### Post by Chunky Dunk on 2008-12-11
First go to System >> Administration >> Printing, and remove all references to that printer, then open up a terminal and "sudo hp-setup". Printing and scanning should both work now.

---

### Post by Hoobes1 on 2008-12-12
how do i delete the references? when i go to Printing, it just opens up the tasts that my printer got.

---

