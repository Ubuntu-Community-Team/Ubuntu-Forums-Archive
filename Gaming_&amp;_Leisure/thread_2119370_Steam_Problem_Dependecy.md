---
title: "Steam Problem Dependecy"
date: 2013-02-23
forum: Gaming &amp; Leisure
---

### Post by ct2034 on 2013-02-23
I am trying do install steam on a frechly installed and fully updated ubuntu 12.10.
I get the message:
```
You are missing the following 32-bit libraries, and Steam may not run:
not
```
What can i do? i guess there is no such package ...

---

### Post by Proots on 2013-02-23
I have the same problem, and allow me to clarify for anyone else-

Upon opening the steam_latest.deb file, the most recent Steam Linux download, it installs and pops up saying 


"Steam Installer
Start Steam to complete installation of the Steam for the current user."

After pressing the "Start Steam" button, which is the only other option from "Close", the error message comes up saying

"You are missing the following 32-bit libraries, and Steam may not run:
not"




I have tried reinstalling Steam (of course), I could not find any updates in 'sudo apt-get upgrade', I have even formatted the computer and reinstalled Ubuntu 12.10 (AMD64). Any help would be much appreciated.

---

### Post by earthmeLon on 2013-02-23
Try:
```
sudo apt-get install ia32-libs
```

---

### Post by CalyxNM on 2013-02-23
I am having these same issues. I tried that terminal command and it didn't work

sudo apt-get install ai32-libs

*then*

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ai32-libs

---

### Post by Proots on 2013-02-23
> **CalyxNM said:**
> I am having these same issues. I tried that terminal command and it didn't work

sudo apt-get install ai32-libs

*then*

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ai32-libs

I believe it is ia32-libs, and I contacted melon to change it. I am installing it now and will report how it goes.


-Cameron


Edit: I ran the code in the terminal and it worked. I went to the error pop-up to close it, and Steam came up doing an update, before the package was even installed. But yes - it works. Many thanks!

---

### Post by CalyxNM on 2013-02-23
You are correct. It is downloading how. 

Hope it works. THANKS!

EDIT: it worked. Downloading TF2 now. 

:)

---

### Post by earthmeLon on 2013-02-23
Thanks guys.  Edited the post.  That should fix your problem.  See you in TF2 :D

---

### Post by CharlesA on 2013-02-23
If you guys have any problems just double clicking the steam deb, install gdebi and install the steam deb with it:

```
sudo gdebi /path/to/steam.deb
```

---

### Post by benelech on 2013-02-23
After trying to run Steam and getting this message twice in a row:

```
You are missing the following 32-bit libraries, and Steam may not run: 
not
```
I pasted the edited line from earthmelon into the terminal, and get this: 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch but it is not installable
E: Unable to correct problems, you have held broken packages.

```I just uninstalled an older version of Ubuntu and reinstalled 12.10 with Win7.

Help me, oh wise ones.

---

### Post by SamuraiMo on 2013-02-23
> **CalyxNM said:**
> I am having these same issues. I tried that terminal command and it didn't work

sudo apt-get install ai32-libs

*then*

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ai32-libs

> **Proots said:**
> I believe it is ia32-libs, and I contacted melon to change it. I am installing it now and will report how it goes.


-Cameron


Edit: I ran the code in the terminal and it worked. I went to the error pop-up to close it, and Steam came up doing an update, before the package was even installed. But yes - it works. Many thanks!

I thank you both, I had the same problem and now it's fixed.

---

### Post by zombifier25 on 2013-02-23
> **benelech said:**
> After trying to run Steam and getting this message twice in a row:

```
You are missing the following 32-bit libraries, and Steam may not run: 
not
```
I pasted the edited line from earthmelon into the terminal, and get this: 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch but it is not installable
E: Unable to correct problems, you have held broken packages.

```I just uninstalled an older version of Ubuntu and reinstalled 12.10 with Win7.

Help me, oh wise ones.

Try updating the cache:
```
sudo apt-get update
```
and try again.

---

### Post by ct2034 on 2013-02-24
Yeah!

its working for me, too.
thank you :)

---

### Post by benelech on 2013-02-24
> **zombifier25 said:**
> Try updating the cache:
```
sudo apt-get update
```
and try again.

I ran that, but nothing changed with steam.

---

### Post by earthmeLon on 2013-02-25
```
sudo apt-get update
sudo apt-get install ia32-libs
```

Please try these two in order and let us know :D

---

### Post by benelech on 2013-03-03
That did it. Thanks for the help everyone. 

10,000 points all each!

---

