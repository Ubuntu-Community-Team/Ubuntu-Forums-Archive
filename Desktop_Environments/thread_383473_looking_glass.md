---
title: "looking glass"
date: 2007-03-13
forum: Desktop Environments
---

### Post by helliewm on 2007-03-13
I am trying to install Looking Glass and keep getting the following error message. I have tired rm -f and auto remove to remove the files that are listed in this error message but that does not work. See attachment. 

Anyone any ideas?

Helen

---

### Post by El_Matthews on 2007-03-13
It's possible that your cache is corrupt. you can clean it with following command:
```
apt-get clean
```
it's possible that you have to put sudo before

---

### Post by helliewm on 2007-03-13
That did not work still getting same error message.

Helen

---

### Post by El_Matthews on 2007-03-13
found on the lg3 website


    * on Ubuntu systems,
          o run the Synaptic Package Manager from the System/Administration menu,
          o click on the Reload button and then
          o Search for lg3d and mark the lg3d-core package for installation.
          o click on the Apply button to download and install


Choosing lg3d-core for installation should automatically choose/mark lg3d-jdk and lg3d-java3d for installation. You will need to accept the 3 licenses for lg3d, jdk and java3d to complete the installation.

you can try by installing first lg3d-java3d and lg3d-jdk but I would gess that there is a problem with the package.

An other possibility is to install it from source: [https://lg3d.dev.java.net/lg3d-getting-started.html](https://lg3d.dev.java.net/lg3d-getting-started.html)

---

### Post by helliewm on 2007-03-13
This is the problem I cannot install through Synaptic Package Manager. Please see the screenshot in my first post for the error message I am getting.

Any ideas at all? I have tried to remove the file that it is the error message but that does not work. 

Helen

---

### Post by wxnker on 2007-03-13
_Stable:_
**deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) stable contrib**

Is this the LG3D repository you use?

adding this repository and Installing with 
```

sudo aptitude update
sudo aptitude install lg3d-core 

```
worked for me with no problems at all.

If you use that repository I have no clue about the error you're getting. Sorry :)

Good luck

Screenshot:
[http://www.ubuntuforums.org/attachment.php?attachmentid=27342&d=1173836199](http://www.ubuntuforums.org/attachment.php?attachmentid=27342&d=1173836199)

---

### Post by hyperair on 2007-11-27
I'm using the unstable repository and Ubuntu Gutsy and I get the same error. I'll post again if I get it working using stable.

---

### Post by Keith Hedger on 2007-11-27
I downloaded the debs directly from the website and they installed perfectly (I didnt use synaptic), but although lg looks very nice its virtually unusable at the moment.

---

### Post by hyperair on 2007-11-27
Where'd you get your debs from? I'm using Gutsy and the Xsession crashed miserably before it could even start. Something about the lg3d-core not being compiled with X11 support properly.

---

### Post by bigken on 2007-11-27
the looking glass looks good but is not very usable give it up your wasting your time

the last time I tried the looking glass I downloaded the sh file double clicked and hey presto it ran

---

### Post by Keith Hedger on 2007-11-27
Cant remember the exact link and ive long since flushed my history cache but these are the debs u need u can do a search for the names:
lg3d-core_1.0.0_i686.deb
lg3d_java3d_1.5.0_i686.deb
lg3d_jdk1.6.0_i686.deb

but as i and bigken said its not very usable

---

### Post by marco999 on 2007-12-22
For me it was a permissions issue with the /bin/arch file. This file needs to be created and 

"uname -m" (without quoutes) needs to be added to the file.

-The permissions for the file are Group - Read and Write, and User -Root read and Write.
-Along with make executable being checked.

Thats how I got it to install.

Thanks to Ashesz for telling me what file to create, where to create it, and what to put in it.


Marco999

---

### Post by nutz on 2008-01-16
Same error here.

---

