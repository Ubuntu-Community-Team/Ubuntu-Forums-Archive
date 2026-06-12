---
title: "Window control disappers"
date: 2011-12-18
forum: Desktop Environments
---

### Post by alwinaugustin on 2011-12-18
Hi,

I am using Ubuntu 9.10 and have installed compiz recently. Now while i am working on machine, the window controls that is the Minimize,Maximize etc will disappear at times and the machine will not respond. Sometimes the issue is fixed when I run compiz from terminal. Sometimes it is not able to open the trminal also and run Compiz. What may the reason for this and how can I fix this..?

Also I have tried to uninstall compiz and when I run it now it is showing  :


alwin.a@4wing57:~$ compiz &
[1] 1953
alwin.a@4wing57:~$ aborting and using fallback: /usr/bin/metacity 

(metacity:1953): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(metacity:1953): atk-bridge-WARNING **: IOR not set.

(metacity:1953): atk-bridge-WARNING **: Could not locate registry

after displaying this the window control will work as normal and the machine will responding normally.

---

### Post by mikewhatever on 2011-12-19
Compiz is a window manager, so when window controls disappear, it is a sign of Compiz quitting unexpectedly. If you want more technical reasons, look through the Xorg log.

PS: Uninstalling Compiz and then trying to run it is ...well, bizarre.:P

---

