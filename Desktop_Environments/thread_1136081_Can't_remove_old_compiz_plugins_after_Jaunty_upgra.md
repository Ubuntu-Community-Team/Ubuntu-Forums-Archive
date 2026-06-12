---
title: "Can't remove old compiz plugins after Jaunty upgrade"
date: 2009-04-24
forum: Desktop Environments
---

### Post by timbalisto on 2009-04-24
I upgraded from 8.10 to 9.04 using the alternate iso, it went well. I want to remove the extra plugins like atlantis, freewins, and elements because they are no longer compatible with Jaunty. I tried to remove them with the terminal
```
tim@tim-desktop:~$ cd /home/tim/compiz/atlantis
tim@tim-desktop:~/compiz/atlantis$ sudo make uninstall
[sudo] password for tim: 
Makefile:48: *** [ERROR] Compiz not installed.  Stop.
tim@tim-desktop:~/compiz/atlantis$ 


```
I don't understand, I have compiz updated to 0.8.2 and everthing else works relatively fine (the effects are slower/choppier, they worked perfect in Intrepid). 
Any ideas as to why I can't remove the old plugins?
Also, could someone point me in the direction to compiz plugins for Jaunty.
Thanks.

---

### Post by reahjw6 on 2009-04-25
Hey

Home folder then Ctrl H find compiz.
Right click sign in as root.
Find the relevent folders and delete plugins and associated files from here.
This worked for me.

---

