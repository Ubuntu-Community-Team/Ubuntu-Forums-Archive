---
title: "Unable to Install Miro After Dist Upgrade"
date: 2009-04-24
forum: General Help
---

### Post by sceptre0 on 2009-04-24
I've been unable to install Miro after updating to 9.04.  It looks like the problem is with this file: /usr/share/applications/miro.desktop.  I tried deleting it, but I get the same error message.  Any ideas?

```
:~$ sudo aptitude install miro
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  miro 
0 packages upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 725kB of archives. After unpacking 3830kB will be used.
Writing extended state information... Done
0% [Waiting for headers]
Get:1 http://us.archive.ubuntu.com jaunty/universe miro 2.0.3-1ubuntu2 [725kB]
Fetched 725kB in 41s (17.3kB/s)                                                 
(Reading database ... 162653 files and directories currently installed.)
Unpacking miro (from .../miro_2.0.3-1ubuntu2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/miro_2.0.3-1ubuntu2_amd64.deb (--unpack):
 trying to overwrite `/usr/share/applications/miro.desktop', which is also in package miro-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for menu ...
Errors were encountered while processing:
 /var/cache/apt/archives/miro_2.0.3-1ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
```

---

### Post by sceptre0 on 2009-04-24
Fixed.  I uninstalled miro-data and installed miro.

---

### Post by abbot on 2009-04-25
I had this problem too and fixed it by uninstalling the miro-data file then re-installing miro.  The only problem is in the process it lost my feed list.  Now unless I can find a data file with my feeds from my previous install I'm gonna have to re-visit dozens of websites to gather feed URLs.  It's not in /.miro

Why did it even uninstall it's self in the first place?

---

### Post by abbot on 2009-04-25
If anyone else looses their feed list like I did, here is a bit of help.  Look for any miro-log files in /.miro.  If there are any in there the one without a number after it should be the most recent one.  Look for any INFO entries that show "update".  It should have all your feed URLs there from the last time miro was ran.  Then you can enter them back in without hunting all over the web.

At least this was the case with me.  Hope it helps.

---

### Post by ddeile on 2009-04-25
Had the same issue with 'miro-data'.  That has been resolved, but am still unable to install Miro due to:

miro: Depends: python (< 2.6) but 2.6.2-0ubuntu1 is to be installed


Python 2.5 and 2.6 are installed on my system.  Anyone know how to resolve this?

---

### Post by tsoul on 2009-04-26
> **ddeile said:**
> Had the same issue with 'miro-data'.  That has been resolved, but am still unable to install Miro due to:

miro: Depends: python (< 2.6) but 2.6.2-0ubuntu1 is to be installed


Python 2.5 and 2.6 are installed on my system.  Anyone know how to resolve this?

Try disabling Miro Repository and installing miro from the ubuntus repository.

---

### Post by ddeile on 2009-04-26
Tried that, when I do I get:

Package miro is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package miro has no installation candidate


Miro looks like it is no longer part of the cannocial-maintained list.  Was it removed due to a conflict with versions of python?

---

### Post by Darth_tater on 2009-04-26
i am having the same problem when trying to install miro!  how soon will the developers be able to push out a new version of the miro package that does not require this old version of python?

---

### Post by Epth Nation on 2009-04-26
> Try disabling Miro Repository and installing miro from the ubuntus repository.

This actually worked for me.  I was getting the python message, and here's what I did:

Disabled the 3rd party Miro repository in software sources.
Opened Synaptic PM and searched for Miro
Marked Miro for complete removal, and Miro-data for removal.  applied updates.
Marked Miro for reinstallation, applied updates.

Miro 2.0.3 is now working, and it kept all my settings.

---

### Post by ddeile on 2009-04-26
Is this an issue with having python 2.5 & 2.6 installed?

Also,  I now seem to have other dependency issues.  Missing:

libboost-datetime1.34.1
libboost-filesystem1.34.1
libboost-python1.34.1
libboost-thread1.34.1

All are needed by Miro.  These are no longer installable from the package manager.  New versions are installed, but the older versions no longer are part of the repository.  Anyone know what package should be listed in my sources to enable these again?

---

### Post by ddeile on 2009-04-27
Solved.

If you are having problems installing Miro on 9.04 you can download packages here:

[http://packages.ubuntu.com/jaunty/miro-data](http://packages.ubuntu.com/jaunty/miro-data)
[http://packages.ubuntu.com/jaunty/miro](http://packages.ubuntu.com/jaunty/miro)

Make sure to install miro-data first.  Your subscriptions should remain, mine did.  

An official Jaunty release for Miro is being worked on by the Miro team per one of the developers blog.

---

### Post by inspired on 2009-04-28
> **ddeile said:**
> Solved.

If you are having problems installing Miro on 9.04 you can download packages here:

[http://packages.ubuntu.com/jaunty/miro-data](http://packages.ubuntu.com/jaunty/miro-data)
[http://packages.ubuntu.com/jaunty/miro](http://packages.ubuntu.com/jaunty/miro)

Make sure to install miro-data first.  Your subscriptions should remain, mine did.  

An official Jaunty release for Miro is being worked on by the Miro team per one of the developers blog.

Thanks for those links.
I found, however, that going that way didn't handle dependency issues.
So I did this:
1) Complete removal of miro using Synaptic
2) Commented out the repository I previously had for miro
3) Added the following repository
deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) jaunty main universe

4) Refresh synaptic
5) Installed Miro using synaptic, and it picked up the missing depencenies and miro-data

Miro is working and all feeds were maintained. I did a backup of /home/username/.miro just in case settings where lost, so I could restore settings. But was not needed.

Regards,

Jonathan  :popcorn:

---

