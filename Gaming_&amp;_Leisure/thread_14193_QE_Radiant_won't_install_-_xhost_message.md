---
title: "QE Radiant won't install - xhost message"
date: 2005-02-05
forum: Gaming &amp; Leisure
---

### Post by sharkzf6 on 2005-02-05
Tried installing QE Radiant 1.4 for Linux on Hoary. After starting, install fails with this message: 
[i]setup.gtk failed to start?
DISPLAY: :0.0
Do you need to issue an xhost + command to let root access X11?
The setup program seems to have failed on x86/glibc-2.1[/i]

The instructions say run the install program as root. I used sudo first, then logged in as root and tried, then issued **xhost localhost** to add the machine to X access. Still same message. Anyone know how to make this work with ubuntu? Thanks.

BTW - I have Doom 3 and Quake 2 installed and running flawlessly with my GF 6800 and 66.29 drivers.

---

### Post by Parantido on 2008-03-06
Hi,

by the way linux-radiant-1.4.0.run package is broken! Problem should be found in other place.

To do the trick you should to extract archive in another folder

./linux-radiant-1.4.0.run --target <folder you like>

Now you have a file (setup.gtk) without exec premission:

chmod +x <folder you like>/setup.data/bin/Linux/x86/glibc-2.1/setup.gtk

Now return in <folder you like> and exec

sh setup.sh

All should work (if doesn't work probably you need libgtk1.2 ...)

Bye

Parantido

---

