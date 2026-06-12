---
title: "Wolfentein enemy territory 2.55"
date: 2011-10-24
forum: Gaming &amp; Leisure
---

### Post by theswarmy on 2011-10-24
Hello fellow ubuntuer's
i know this has been posted before and i tried what it said there but im still getting a few error i've tried to install the .run (was mentioned before to ignore the error so i did) and when i try to run it it says

```


ET 2.55 linux-i386 May 27 2003
----- FS_Startup -----
Current search path:
/home/hei/.etwolf/etmain
/home/hei/.Games/et/etmain

----------------------
0 files in pk3 files
----- CL_Shutdown -----
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: Couldn't load default.cfg - I am missing essential files - verify your installation?

```

any way to fix this? or install it correctly? when i try to install it it gives this error

```


Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
It is recommended to install as the super user
Please enter the root password or hit enter to continue as is
Password: 
su: Authentication failure
This installation doesn't support glibc-2.1 on Linux / unknown
(tried to run setup)
See http://zerowing.idsoftware.com/linux/ for troubleshooting
The setup program seems to have failed on unknown/glibc-2.1

See http://zerowing.idsoftware.com/linux/ for troubleshooting

```

thank you for the replies.
--swarmy

---

### Post by ubudog on 2011-10-24
*Thread moved to Gaming & Leisure.*

---

### Post by Perfect Storm on 2011-10-25
Sounds like a borked download, other than that; you're downloading an old version of ET.

For easy install of the latest try PlayDEB: [http://www.playdeb.net/updates/ubuntu/11.10/?q=enemy](http://www.playdeb.net/updates/ubuntu/11.10/?q=enemy)

---

### Post by ubudog on 2011-10-25
> **Artificial Intelligence said:**
> 
For easy install of the latest try PlayDEB: [http://www.playdeb.net/updates/ubuntu/11.10/?q=enemy](http://www.playdeb.net/updates/ubuntu/11.10/?q=enemy)

+1 for PlayDeb.  Some awesome games there.

---

### Post by alexvy13 on 2011-10-25
hope they update alien arena on playdeb

---

### Post by Perfect Storm on 2011-10-25
> **alexvy13 said:**
> hope they update alien arena on playdeb

You're posting in the wrong thread, the Alien Arena thread is just down the list ;)
Bug report if you wish to see a newer package.

---

### Post by theswarmy on 2011-10-25
> **Artificial Intelligence said:**
> Sounds like a borked download, other than that; you're downloading an old version of ET.

For easy install of the latest try PlayDEB: [http://www.playdeb.net/updates/ubuntu/11.10/?q=enemy](http://www.playdeb.net/updates/ubuntu/11.10/?q=enemy)

well the thing is that most of the servers i used to play on Windows were from 2.55 (FBI/WoD etc) 2.60 has different servers on it hence why i wanted 2.55 to work.

---

### Post by Perfect Storm on 2011-10-25
Are you running a 64/bit Ubuntu system?

---

### Post by theswarmy on 2011-10-25
> **Artificial Intelligence said:**
> Are you running a 64/bit Ubuntu system?

Yes i am, Ubuntu 10.10 X64

---

### Post by Perfect Storm on 2011-10-25
Have you installed 32bit libraries as ET is a 32bit application.

---

### Post by theswarmy on 2011-10-25
Well it seems theres a few options to install the 32bit libraries, i tried one and it says "ia32-libs is already the newest version."
i am now trying "getlibs" to see if that works i'll post the results


edit: well according to getlib there are no packages to install for W:ET

---

### Post by theswarmy on 2011-10-25
I downloaded the .exe from the wolfenstein site and that seems to have installed and works fine i guess i'll have to use Wine rather then the native install for the game

---

### Post by Perfect Storm on 2011-10-26
Though you're getting it to work with wine.
If you still want to try to getting to work nativity:

```
linux32 sh <file>
```

OR

```
sh <file> --keep
```

go to something similar path like this:
setup.4662/setup.data/bin/Linux/x86/setup

run the setup file in there like:
```
linux32 sh <file>
```

---

