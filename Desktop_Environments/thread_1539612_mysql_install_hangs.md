---
title: "mysql install hangs"
date: 2010-07-26
forum: Desktop Environments
---

### Post by darksidedude on 2010-07-26
hey all, I am trying to install mysql on my desktop computer/server
just to be clear I am using the desktop install disk, the one with the fancy GUI

here is what I did 
```
Sudo apt-get install mysql-common
```

and here is the output that it shows me and hangs at

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-common is already the newest version.
mysql-common set to manually installed.
The following packages were automatically installed and are no longer required:
  libhtml-template-perl mysql-server-5.1 mysql-server-core-5.1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mysql-server-5.1 (5.1.41-3ubuntu12.3) ...

```

any help would be appreciated, thanks

---

### Post by deadtom on 2011-05-01
Did you ever find a solution to this? I'm having the same problem today.

---

### Post by smallfonts on 2011-10-09
Hello! I had the same problem from "apt-get install mysql-server" (ubuntu 11.04 32bit) and it hangs at exactly the same part!

However, a stroke of luck led me to solve this issue! All i did was to 

1) Run "apt-get install mysql-server" until the part where it hangs
2) Open up a new terminal window (while the installer is still running on the other window)
2) run "start mysql"

At this point i realized that the installer actually carried on and finished its installation! yeay!

3) restart ubuntu and its good to go!

hope my solution would apply to yours too!

---

