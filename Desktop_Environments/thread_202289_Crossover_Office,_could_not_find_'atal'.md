---
title: "Crossover Office, could not find 'atal'"
date: 2006-06-23
forum: Desktop Environments
---

### Post by Lamber on 2006-06-23
Hello, 

a few days ago i've installed Ubuntu 6.06 from scratch after messing up my home directory with some stupid chmod tests ](*,) 

Today i've downloaded the Crossover Office demo from codeweavers.com. The download went fine, no errors were given. But when i'm trying to execute the .sh file i get this error:

> 
robert@robert:~/Desktop$ LANGUAGE=C sudo sh inst*.sh /home/robert
Verifying archive integrity...OK
Uncompressing CrossOver Office Professional......................................
Couldn't load 'atal'

*note: the 'LANGUAGE=C' is because I use Dutch as language, the error is the same in Dutch*

Searching on google and several linux and computersite's won't give me any information about 'atal'. apt-get install atal didn't worked also (even this was a wild guess)

Can someone help my by saying what 'atal' actually is, and what i can do to prevent getting this odd error?

Some specs may be usefull:

Ubuntu 6.06 with Gnome as windowmanager
AMD Athlon XP 2400+
1024 MB + 256 MB of memory
160 GB HD

Okay, found the solution:

chmod a+x the installation script
then run: ./install*.sh

---

### Post by fares on 2006-06-23
Hi there,

it could be that the file you downloaded is corrupted, I'd try downloading another copy from the Codeweavers' website.

PS - You don't have to install Crossover Office Pro as "root", you can just perform a single user installation (easier to keep under control, imho).

---

### Post by patrick295767 on 2006-06-23
[QUOTE=Lamber]Hello, 

a few days ago i've installed Ubuntu 6.06 from scratch after messing up my home directory with some stupid chmod tests ](*,) 

Today i've downloaded the Crossover Office demo from codeweavers.com. The download went fine, no errors were given. But when i'm trying to execute the .sh file i get this error:


*note: the 'LANGUAGE=C' is because I use Dutch as language, the error is the same in Dutch*

Searching on google and several linux and computersite's won't give me any information about 'atal'. apt-get install atal didn't worked also (even this was a wild guess)

Can someone help my by saying what 'atal' actually is, and what i can do to prevent getting this odd error?

Some specs may be usefull:

Ubuntu 6.06 with Gnome as windowmanager
AMD Athlon XP 2400+
1024 MB + 256 MB of memory
160 GB HD

Okay, found the solution:

chmod a+x the installation script
then run: ./install*.sh[/QUOTE]
  
I didnt try it like this.
  
Once installed Did you try to run the sh script via :
```
sh -c /opt/cxoffice ....  bla bla .sh
```
  
Not installed: 
> sh scriptinstallation.sh

---

