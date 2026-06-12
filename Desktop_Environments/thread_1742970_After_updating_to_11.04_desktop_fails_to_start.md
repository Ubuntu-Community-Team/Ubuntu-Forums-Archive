---
title: "After updating to 11.04 desktop fails to start"
date: 2011-04-29
forum: Desktop Environments
---

### Post by vikkmaugli on 2011-04-29
Hi!

I've just updated to 11.04 from 10.10.
After restarting desktop does not start.
It says [OK] for every command line, but nothing 'graphical' happens
On and other console I tried: 
```
sudo service gdm start
```
answer: ```
gdm start/running, process 2032
```
 ```
sudo service gdm stop
```
answer: ```
gdm stop/waiting
```

Any idea?

Thanks!

---

### Post by ajgreeny on 2011-04-29
What happens if you use command ```
startx
``` after starting gdm?

---

### Post by vikkmaugli on 2011-04-30
Thnx!
Not solved the problem, but I could realize from error msg that problem with nvidia driver.
After reinstalling nvidia, gnome started, but with no sidebars and Ctrl-Alt-T cannot bring out console. 
Other idea for that? :)

---

### Post by Krytarik on 2011-04-30
So, Compiz is not running. Try creating a launcher for the command "compiz --replace" at your desktop, and launching it.

Greetings.

---

### Post by electrojustin on 2011-04-30
Make sure you have ccsm installed, then try creating a launcher for ccsm. From there enable the unity plugin.

---

### Post by Krytarik on 2011-05-01
> **electrojustin said:**
> Make sure you have ccms installed, then try creating a launcher for ccms actually. From there enable the unity plugin.
+1  more likely, there are just too many fail scenarios just now

To check if "CompizConfig Settings Manager" is installed, create a launcher for "gnome-terminal", launch it, then run:
```
dpkg -l |grep compizconfig-settings-manager
```To install CCSM:
```
sudo apt-get install compizconfig-settings-manager
```Notice that the actual command to launch it is indeed "ccsm".

Also, when running CCSM, check if any other plugins need to be re-enabled as well.

---

