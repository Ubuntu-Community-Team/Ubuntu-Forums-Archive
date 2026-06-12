---
title: "PPD printer driver mismatch. Gutenprint"
date: 2009-01-20
forum: General Help
---

### Post by Slopies on 2009-01-20
Hi (sorry for my english),
I installed gutenprint 5.2.3 with sources because... I didn't noticed the version 5.2.0 was already installed (I'm with Interpid). I decided  I preferred the 5.2.0 because it was the one maintained by canonical for Ubuntu 8.10. Then, I tried to uninstall it (5.2.3) the best I could with a **make uninstall** (maybe I'm noob :p ).
After, I tried to print something. It didn't work.
Here the diagnostic: ijsgutenprint:the version of Gutenprint software installed (5.2.0-rc1) does not match the PPD file (5.2.3).

I tried **apt-get install -reinstall ijsgutenprint**
I tried the same with cups-driver-gutenprint or libgutenprint2... it changed nothing.
I tried some **apt-get remove**: there is a dependence with ubuntu-desktop. I thought it wasn't a good idea to do it :p

Any other idea?
thx


[SIZE="1"]Yeah, I didn't know which name chose, thus I copied this one: [http://ubuntuforums.org/showthread.php?t=984519&highlight=ppd+gutenprint](http://ubuntuforums.org/showthread.php?t=984519&highlight=ppd+gutenprint)[/SIZE]

---

### Post by wolfen69 on 2009-01-20
> **Slopies said:**
> 
I tried some **apt-get remove**: there is a dependence with ubuntu-desktop. I thought it wasn't a good idea to do it :p


it won't remove ubuntu-desktop, it's just referring to the meta-package. i have seen this many times. it won't remove your desktop. go ahead and do it.

after uninstalling a package, it's a good idea to do ```
sudo apt-get clean && sudo apt-get autoremove
``` it will clean the cache and unused dependencies, insuring you get all new files for reinstall.

---

### Post by Slopies on 2009-01-21
Okay. I autoremove all of them, I clean, and I reinstalled all of them. When I install cups-driver-gutenprint, it says "Did not update any PPD files".

You are sure it is the solution? If I knew how, I think I would simply try to replace manually the PPD...

---

### Post by Slopies on 2009-01-21
Okay, I fixed it!
I write my solution for anybody who would have the same problem in the future.

I don't know what worked and I don't want to recreate the problem just for fun. So, try it first: after had reinstalled the old drivers, do system->administration->printing and just "delete" the printer and add a "new" one.
If it doesn't work, find the sources (in my case it was 5.2.0**-rc1**. You may not find -rc1 versions on gutenprint's website. I'm not sure to know what they are), install it, and... uninstall it. Then, reconfigure your printer with system->administration->printing.

I know it's a little bit dirty, but I found nothing better.

---

### Post by aceqbaceq on 2009-06-04
> **Slopies said:**
> Hi (sorry for my english),
I installed gutenprint 5.2.3 with sources because... I didn't noticed the version 5.2.0 was already installed (I'm with Interpid). I decided  I preferred the 5.2.0 because it was the one maintained by canonical for Ubuntu 8.10. Then, I tried to uninstall it (5.2.3) the best I could with a **make uninstall** (maybe I'm noob :p ).
After, I tried to print something. It didn't work.
Here the diagnostic: ijsgutenprint:the version of Gutenprint software installed (5.2.0-rc1) does not match the PPD file (5.2.3).

I tried **apt-get install -reinstall ijsgutenprint**
I tried the same with cups-driver-gutenprint or libgutenprint2... it changed nothing.
I tried some **apt-get remove**: there is a dependence with ubuntu-desktop. I thought it wasn't a good idea to do it :p

Any other idea?
thx


[SIZE="1"]Yeah, I didn't know which name chose, thus I copied this one: [http://ubuntuforums.org/showthread.php?t=984519&highlight=ppd+gutenprint](http://ubuntuforums.org/showthread.php?t=984519&highlight=ppd+gutenprint)[/SIZE]



i had the same problem : The version of Gutenprint software installed (5.2.3) does not match the PPD file. 

as i understand  the source of problem is : in the foomatic database version of driver does not match the driver system (gutenprint). so we need update gutenprint , in my case perfectly works the following solution:

#apt-get install ijsgutenprint

#apt-get install foomatic-db

#apt-get install cups-driver-gutenprint


but i suppose that only 

#apt-get install cups-driver-gutenprint

is really needed.

---

