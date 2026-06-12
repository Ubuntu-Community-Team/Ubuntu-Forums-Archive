---
title: "Dell GX240 Cannot enable graphics support. (v. 10.10)"
date: 2010-12-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bluemystic01 on 2010-12-29
I don't know if it is hopeless to want to run graphics on this, but I wanted to see if someone has. It is a Dell GX240 with integrated video, and I cannot even put desktop graphics into normal. I have seen other threads where they ask for somethings, so I am pasting what I get when I enter compiz into terminal. Please tell me if it is hopeless or not. Or if there are listed minimum hardware requirements. 

joseph@joseph-OptiPlex-GX240:~$ compiz
compiz (core) - Fatal: Support for non power of two textures missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager


P.S. Other than this I love Linux. I know it's an old computer, so I am not too worried. Just want to check.

---

### Post by 67GTA on 2011-01-03
It is probably useless. Ubuntu blacklisted the 845 for compiz. If it is just a hobby machine, and you feel brave, you could try this hack: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1128253](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1128253)

---

