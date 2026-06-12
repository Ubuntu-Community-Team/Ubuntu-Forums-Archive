---
title: "keepe gettign this error when compiling things!!"
date: 2006-10-02
forum: Desktop Environments
---

### Post by searayman on 2006-10-02
I keep getting this error when i compile things!

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!


so how can i fix this?

---

### Post by black hole sun on 2006-10-02
Why do you want to compile whatever it is you're trying to compile...?

If you insist, then you need the X11 development packages. Search synaptic for all things x11 with a -dev suffix and install them.

---

### Post by searayman on 2006-10-03
ok, also with another item i get this error:

mike@mike-desktop:~$ kxdocker
KXDocker Will use Composite Extensions!
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kxdocker: WARNING: Cannot find updated resources: you may need to update or reinstall KXDocker resources, checkout [http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources](http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources)
kxdocker: WARNING: loading xml...
kxdocker: WARNING: Warning user kxdocker_conf.xml may be corrupt: loading last backup!
kxdocker: WARNING: Warning user, and backup configurations are corrupt! I'm going to load system kxdocker_conf.xml !!!
kxdocker: WARNING: Warning user, backup, system configurations are corrupt! please install right kxdocker_conf.xml
ERROR: Communication problem with kxdocker, it probably crashed.
mike@mike-desktop:~$      


what can i do for thsi one?

---

### Post by podunk on 2006-10-03
If you're trying to install Kxdocker in __Ubuntu___ you're going to be disappointed I think. It works great in Kubuntu though! :-)

Why don't you use your package manager to install it?

In Kubuntu
Kmenu (Start for us winduhs folks :-) )
System
Adept (Package Manager)

When it opens search for kxdocker
Right click it and chose install.

Looking at your compile output &#8211; did you install the package
build-essential
from the package manager?

I don't know enough to tell who knows more than I do yet &#8211; so don't be offended by this link:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by searayman on 2006-10-03
ok i already had kxdocker insatlled from the apt-get but i didnt have build-essentilas, so i did a sudo apt-get remove kxdocker then sudo apt-get install build-essentils. Then after i installed build essentials i tried re-installign kxdocker from apt-get and i did. then i ran kxdocker, and i got the same error. ANd by the way i am on kubuntu.

mike@mike-desktop:~$ kxdocker
KXDocker Will use Composite Extensions!
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kxdocker: WARNING: Cannot find updated resources: you may need to update or reinstall KXDocker resources, checkout [http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources](http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources)
kxdocker: WARNING: loading xml...
kxdocker: WARNING: Warning user kxdocker_conf.xml may be corrupt: loading last backup!
kxdocker: WARNING: Warning user, and backup configurations are corrupt! I'm going to load system kxdocker_conf.xml !!!
kxdocker: WARNING: Warning user, backup, system configurations are corrupt! please install right kxdocker_conf.xml
ERROR: Communication problem with kxdocker, it probably crashed.
mike@mike-desktop:~$

---

### Post by searayman on 2006-10-04
did i stump u guys with this one?

---

### Post by russianbandit on 2006-10-24
I am seeing the same problem with Kxdocker. I'm running Edgy Kubuntu and istalled it trought the Adept from repos.
Any fixes for this yet?

---

### Post by floflooo on 2006-10-26
Same exact problem here...

---

