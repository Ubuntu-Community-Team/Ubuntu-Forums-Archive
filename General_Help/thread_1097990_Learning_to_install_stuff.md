---
title: "Learning to install stuff"
date: 2009-03-16
forum: General Help
---

### Post by forestwalkerjoe on 2009-03-16
I am still rather new.. so there are things that baffle me. 
this one is not as simple as i would have thought. 
I have Ubuntu 8:10 wubi.. from an XP system. 
here is a link to a linux ap i would like to use and have no idea why it fails when i use the install code that is listed. 
i am sure this is some sort of dependencie thing.. but could use some help with why and what to do to get it running. thanks 
I read a lot.. i also have a PDA with Adobe and a few other Ereaders on it. i am fast moving from using windows for much of anything.. so i am trying to get all the stuff i use in windows working in Ubuntu. 
This was posted on a linnk in Downloadsquad showing how to order and convert most ereader styled books and RSS into compatible reader books. 
here is the link to install.. but i need your help to find out why its not installing. it says it doesnt have setuptools.. but if i apt get the setuptools it fails to find package. I have to assume its a Janty only thing? 
[http://calibre.kovidgoyal.net/download_linux]("http://calibre.kovidgoyal.net/download_linux")
If ya'all can show me how to do the full install.. and or why it would not work on mine.. I'd be very happy.. 
again thank 
you
FWJ

---

### Post by jonobr on 2009-03-16
post the errors your seeing when your doing the installation, that may help.

Also I notice the thing refers to differences in 32-64 bit installs, recommend you post which you are running.

I would stringly recommend trying to do all installation work through synaptic , however, like this app, there are some that are not there and you have to go through this.

Did you notice in the guide it indicates you will get some failures?

Anyway , first things first, you should post your errors

---

### Post by oldos2er on 2009-03-16
One reason for not finding a package is not having all repositories enabled. Check System, Administration, Software Sources.

---

### Post by forestwalkerjoe on 2009-03-17
ok.. i thought i had all the resposits in there.. i am seeing an odd thing in the repositories update.. it not validating all the repositories.. not sure why or what that means.. 
when i use that code on second half of the link i sent you you.. it starts all the downloads and so on.. and gets to this point.. and then fails. 
 ```
2009-03-17 12:31:59 (263 KB/s) - `-' saved [7129980/7129980]

calibre-0.5.1/src/pyPdf/utils.py
calibre-0.5.1/src/pyPdf/xmp.py
calibre-0.5.1/todo
calibre-0.5.1/upload.py
rj@ubuntu:~$ cd calibre*
rj@ubuntu:~/calibre-0.5.1$ python setup.py build && sudo python setup.py installSetup calibre version: 0.5.1
Traceback (most recent call last):
  File "setup.py", line 49, in <module>
    from setuptools import setup, find_packages
ImportError: No module named setuptools
rj@ubuntu:~/calibre-0.5.1$ sudo calibre_postinstall
sudo: calibre_postinstall: command not found
rj@ubuntu:~/calibre-0.5.1$ 

``` 
I am going to have to assume there is some thing wrong with my update thing. 
i know there are "dependencies " it needs.. but i am just not that experienced in Ubuntu Linux yet to know how to do all that. 
IN the sources thing.. i added some 3erd party stuff and some are not validating.. give me errors.. and i am sure this is also part of it.
If i go into the sy package manager and do a reload i get this sort of error.. 
 ```
W: GPG error: http://wine.budgetdedicated.com intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 71346C8340130828
```
If i search for the dependencies listed below the LINKED CODE on that page they fail.. 
I think some where i messed up some thing..and heck if i didnt just get this wubi working again! 

FWJ

---

