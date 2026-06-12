---
title: "mojo.run files"
date: 2013-03-15
forum: Gaming &amp; Leisure
---

### Post by ninjaondemand on 2013-03-15
I've tried the software center, and the archive manager, and searching for applications online. Does anyone know how to open mojo.run files? :confused:

---

### Post by Perfect Storm on 2013-03-15
You need the terminal for this;
```
chmod +x mojo.run
./mojo.run
```

Depending where the file is you need to change directory as well. Like **cd Downloads**

---

### Post by BCRailrodder on 2013-03-15
Hi Guys,

I've just gotten through the Humble Bundle as well and have gotten it to unpack and seemingly install HOWEVER (you knew there was going to be one, didn't you :) ) when I go to start the game from the dashboard in Unity nothing happens.  When I go to the directory it installed in and click on the script and "run in terminal" you can see the terminal start then shutdown right away (just a flicker really).  When I click on the script and then "run", nothing happens.

Any further thoughts?

Thanks,

Kent

---

### Post by Perfect Storm on 2013-03-16
>  installed in and click on the script and "run in terminal" you can see the terminal start then shutdown right away (just a flicker really). 

Instead, find the terminal, drag the launcher into the terminal and hit <enter>.

---

### Post by BCRailrodder on 2013-03-16
Thanks for the advise.  I tried it and ended up with the following error
"error while loading shared libraries: libpulse-simple.so.0: cannot open shared object file: No such file or directory"

I've done a search on my system (12.04 btw) as well as synapitic with no luck.

Kent

---

### Post by Perfect Storm on 2013-03-16
Are you using 64-bit?

---

### Post by BCRailrodder on 2013-03-16
Yes I am.  

I am hoping that you aren't going to tell me that it's only available for the 32 bit systems?

I did check out the dependancies for the game and while  libc-2.12.2 is to the newest version, the newest version for  libstdc++.6.0.13 is libstdc++6 4.6.3-1ubuntu5 (I think) which I did install.

Kent

---

### Post by Perfect Storm on 2013-03-16
You properly need to install 32-bit libs as I'm pretty sure the game is 32-bit only.
But try locate libpulse-simple on your system.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=240266&stc=1&d=1363486577[/IMG]

The name of the to install is **libpulse0:i386**
To get all the 32-bit compatible on a 64-bit you can install the meta-package **ia32-libs**
```
sudo apt-get install ia32-libs
```

---

### Post by BCRailrodder on 2013-03-18
Thank you, Thank you, Thank you.

That is exactly what I needed.. I am now a happy camper <G>.

Kent

> **Artificial Intelligence said:**
> You properly need to install 32-bit libs as I'm pretty sure the game is 32-bit only.
But try locate libpulse-simple on your system.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=240266&stc=1&d=1363486577[/IMG]

The name of the to install is **libpulse0:i386**
To get all the 32-bit compatible on a 64-bit you can install the meta-package **ia32-libs**
```
sudo apt-get install ia32-libs
```

---

