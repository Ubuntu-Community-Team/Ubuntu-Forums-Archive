---
title: "New Install ubuntu 11.04 with Unity"
date: 2011-08-01
forum: Desktop Environments
---

### Post by DaveVentresca on 2011-08-01
Ok, 
  This problem has been stumping me for days... Trying to install Skype through the software center, but I keep getting this:
----------------------------------------------------------------------------------------------------

The following packages have unmet dependencies:

skype: Depends: libc6 (>= 2.4) but 2.13-0ubuntu13 is to be installed
       Depends: libgcc1 (>= 1:4.1.1) but 1:4.5.2-8ubuntu4 is to be installed
       Depends: libqt4-dbus (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.2 is to be installed
       Depends: libqt4-network (>= 4:4.5.3) but 4:4.7.2-0ubuntu6 is to be installed
       Depends: libqtcore4 (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.2 is to be installed
       Depends: libqtgui4 (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.2 is to be installed
       Depends: libstdc++6 (>= 4.2.1) but 4.5.2-8ubuntu4 is to be installed

----------------------------------------------------------------------------------------------------


  Anyone else running into this issue?
   
      -Dave

---

### Post by DMGrier on 2011-08-02
I have these problems sometimes too with some software and the fix for me usually using terminal instead.
> sudo apt-get update && sudo apt-get install skype

---

### Post by DaveVentresca on 2011-08-02
Tried that too... Here's the output after sudo apt-get install skype:
------------------------------------------------------------------------------------------
ogion@Ogion:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype : Depends: libqt4-network (>= 4:4.5.3) but it is not going to be installed
E: Broken packages
ogion@Ogion:~$ 
 
--------------------------------------------------------------------------------------------------

Any ideas?

---

### Post by wildmanne39 on 2011-08-02
Hi,open synaptic click edit, fix broken packages and see if that works.

---

