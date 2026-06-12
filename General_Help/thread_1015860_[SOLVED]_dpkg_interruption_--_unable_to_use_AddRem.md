---
title: "[SOLVED] dpkg interruption -- unable to use Add/Remove: MAJOR FAILURE"
date: 2008-12-19
forum: General Help
---

### Post by chaplanger on 2008-12-19
I am running UBUNTU 8.10

I was attempting to update install restricted formats as per the Community Ubuntu Documentation ([https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)) following the advice for using the terminal.  When installing the JAVA updates -- the terminal hung at the 'agreement screen' where 'Ok' needs to be chosen -- nothing I could do would enable the terminal to accept any type of Ok command (that I could think of) 

I eventually gave up and shut down terminal (This turned out to be a huge mistake).  Now I receive error messages when attempting to use Add/Remove:  Here is the message:
-----------------
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
---------------------

When I follow the above instructions I run into roadblocks.  I go into terminal to run 'sudo apt-get update'   I am told:
-------------
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
----------------

When I try to run this I am told that superuser privilege is required.  My password (which works with SUDO fails to be recognized (it includes upper and lower case letters, numbers and two symbols - the symbols do not seem to be recognized as it returns the 'password' without the symbols included.

How do I fix this broken installation?  I have no idea how to fix this problem.

---

### Post by chaplanger on 2008-12-19
Running Synaptic Package Manager returns the following error:

---------------------------
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
---------------------

Help!

---

### Post by redilyn on 2008-12-19
I've done the same before. Fixed it simply by issuing the following.

```
sudo dpkg --configure -a
```

If your password still won't work try this

```
sudo -s
dpkg --configure -a
```

---

### Post by decoherence on 2008-12-19
it's ok to interrupt the process while packages are downloading, but if you interrupt it while it's installing, you'll get the message you had.

First off, that java license screen. This has cause trouble for more people than you today. To move around elements in the command line, use the tab key. So when that license comes up, read it (haha) press tab so that OK is highlighted, then enter.

Now, to fix your setup run

```
sudo dpkg --configure -a
```

and copy/paste any errors here. next run

```
apt-get -f install
```

and copy/paste any errors

Sometimes the packaging system gets confused but it can always be fixed, at least in my eight years of experience with debian.

---

### Post by chaplanger on 2008-12-19
Redilyn & Decoherence,
Thanks so much -- I was able to use 'sudo -s' to get in as root and then using the commands you both cited, was able to fix the problem and complete the java installation (thanks for the insight on how to move around that screen!)

Blessings to you both!

---

