---
title: "Update my Conky from 1.6.1 to 1.7.2, HOW?"
date: 2009-09-14
forum: Desktop Environments
---

### Post by ImbaDaimon on 2009-09-14
One week ago i install Conky by terminal command ```
sudo apt-get install conky
``` and i start testing the software.

Today i realise that the version i had installed it was **1.6.1** but the latest version is [**1.7.2**]("http://conky.sourceforge.net/").

I download the latest files [**conky-1.7.2.tar.bz2**]("http://sourceforge.net/projects/conky/files/conky/") and extract it. When i try to install it *./configure* a messege apear on terminal:
**No package 'lua5.1' found**

i try this command ```
sudo apt-get install lua5.1
``` but i get this messege
```
lua5.1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```



Could anyone help me? Is there any other way to update my Conky?

---

### Post by theZoid on 2009-09-14
[Go here and add the repo]("https://launchpad.net/~norsetto/+archive/ppa")...follow instructions for key, then

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ImbaDaimon on 2009-09-16
Ty

Succesfully upgraded my Conky :D

---

### Post by AlphaLexman on 2009-09-22
Worked for me too.

Thank you.

---

### Post by Kaizzer on 2009-10-08
> **theZoid said:**
> [Go here and add the repo]("https://launchpad.net/%7Enorsetto/+archive/ppa")...follow instructions for key, then

```
sudo apt-get update
sudo apt-get upgrade
```

this may sound like really newbie question...but still .. this procedure will work for upgrading from conky 1.5.1 on Ubuntu 8.04. ?? 

thanks in advance..

---

### Post by Kaizzer on 2009-10-08
Looks like that is not available for 8.04 .. 
Does anyone knows a work around?  .. TIA.

---

### Post by EmEyKeYwAy on 2009-11-08
> **Kaizzer said:**
> Looks like that is not available for 8.04 .. 
Does anyone knows a work around?  .. TIA.

Yes, there is.

Add this to your /etc/apt/sources.list :

deb [http://ppa.launchpad.net/norsetto/ppa/ubuntu](http://ppa.launchpad.net/norsetto/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/norsetto/ppa/ubuntu](http://ppa.launchpad.net/norsetto/ppa/ubuntu) jaunty main

---

