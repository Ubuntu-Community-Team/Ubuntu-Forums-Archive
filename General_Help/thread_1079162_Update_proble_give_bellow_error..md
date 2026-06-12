---
title: "Update proble give bellow error."
date: 2009-02-24
forum: General Help
---

### Post by ravindukelum on 2009-02-24
When I going to my buntu 8.10 it gives following error.
```
dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report
```

and I tried ```
dpkg --configure -a
``` and it did not work an I reprt this in Launchpad and somebody send me a mail saying that bug was fixed and some more details and I have no idea about those details tell me how to solve this error.

Here is that person's reply.


```
This bug was fixed in the package dpkg - 1.14.20ubuntu6.1

---------------
dpkg (1.14.20ubuntu6.1) intrepid-proposed; urgency=low

 * deal with dpkg database in inconsitent state
   (git commit 4c93e0ea1c95dd9259ae0424766913ade140a4b3)
   LP: #323894

 [ Guillem Jover ]
 * When loading the status file fix up any inconsistent package in state
   triggers-awaited w/o the corresponding package with pending triggers.
   Closes: #487637, #486843, #489068

 -- Michael Vogt <michael.vogt@ubuntu.com>   Wed, 04 Feb 2009 09:30:15
+0100

** Changed in: dpkg (Ubuntu Intrepid)
      Status: Fix Committed => Fix Released

```

---

### Post by plucky on 2009-02-24
Have you tried to search for a solution on the forums?


From a terminal window use ```
sudo dpkg --configure -a
``` enter your login password which will not echo and see if that fixes the problem.

If you get any errors,then copy and paste them to the forum so that we can see what they are.


Good Luck

---

### Post by ravindukelum on 2009-02-24
> **plucky said:**
> Have you tried to search for a solution on the forums?


From a terminal window use ```
sudo dpkg --configure -a
``` enter your login password which will not echo and see if that fixes the problem.

If you get any errors,then copy and paste them to the forum so that we can see what they are.


Good Luck

I tried ```
sudo dpkg --configure -a
```so many time but it did not work it gives same message again and again.and gives followin error also.

```
Setting up python-simplejson (1.9.1-1) ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: Trying to overwrite simplejson/encoder.py which is already provided by /usr/share/python-support/lanshark
dpkg: error processing python-simplejson (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted
```

---

### Post by plucky on 2009-02-24
Try ```
sudo dpkg --purge remove python-simplejson
```


See this [link](http://techxplorer.com/2006/05/21/resolving-an-odd-dpkg-error-in-ubuntu/)

Good Luck

---

### Post by ravindukelum on 2009-02-24
> **plucky said:**
> Try ```
sudo dpkg --purge remove python-simplejson
```


See this [link](http://techxplorer.com/2006/05/21/resolving-an-odd-dpkg-error-in-ubuntu/)

Good Luck
 Any dpkg command does not work now.

---

### Post by plucky on 2009-02-24
You could try ```
sudo apt-get -f install
``` or open Synaptic package manager and use the "Fix broken packages" option if dpkg will let you.


Good Luck

---

