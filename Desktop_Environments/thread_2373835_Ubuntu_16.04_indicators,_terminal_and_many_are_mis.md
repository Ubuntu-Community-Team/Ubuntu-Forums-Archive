---
title: "Ubuntu 16.04 indicators, terminal and many are missing"
date: 2017-10-10
forum: Desktop Environments
---

### Post by karthikkb93 on 2017-10-10
My Ubuntu 16.04 was working perfectly yesterday and today morning when i switched it on, i cannot find the shut down button or anything else on the top panel. I am not able to open terminal with ```
ctrl+alt+T
``` or from launcher. When i am searching something in the launcher, all it says is not found. I am have done the installation of ubuntu through wubi. In the login page all the buttons are present. I have tried reinstalling ubuntu-desktop and indicator-session, but the issue remains. My hardisks are also not shown, but it is showing in /dev/sd*. [ATTACH=CONFIG]277062[/ATTACH][ATTACH=CONFIG]277063[/ATTACH][ATTACH=CONFIG]277064[/ATTACH][ATTACH=CONFIG]277065[/ATTACH] Please help me with this. I have done some cross compiling yesterday with sysroot. If that makes any difference.

Thank you for your time.

---

### Post by karthikkb93 on 2017-10-10
I was able to solve this issue. As suspected the Ubuntu was going for the sys-root i have used for some cross compilation. I came to this conclusion by deleting the sysroot used for the cross compilation, the ubuntu works normally. I have no idea why ubuntu is going for the sysroot. 

Thank you.

Update : 
I was wrong. The bin path in the sysroot was exported in /etc/profile. The sysroot bin path and ubuntu bin paths were having same bin files. I guess the OS was confused which one to use.

---

