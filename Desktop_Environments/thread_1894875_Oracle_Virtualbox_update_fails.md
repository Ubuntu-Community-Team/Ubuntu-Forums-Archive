---
title: "Oracle Virtualbox update fails"
date: 2011-12-13
forum: Desktop Environments
---

### Post by intruderukr on 2011-12-13
I have Vb hosted on Oneric running on my inspiron e1405.  I'm unable to update Virtualbox 4.1.2 from Oracle, when I try to update this is the message I get:
[HTML]W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/oneiric/Release  Unable to find expected entry 'contrib/source/Sources' in Release file (Wrong sources.list entry or malformed file)
[/HTML]
I need Virtualbox for a few Windows tasks, but if I can't get this working I'll have to go back to double booting... :(
Please help...

---

### Post by oldtimer7777 on 2011-12-13
Did you install it from the PPA?

This walk-through has it listed about 2/3rds the way down the checklist.  I tried it yesterday, and it installed fine from the PPA.

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

> **intruderukr said:**
> I have Vb hosted on Oneric running on my inspiron e1405.  I'm unable to update Virtualbox 4.1.2 from Oracle, when I try to update this is the message I get:
[HTML]W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/oneiric/Release  Unable to find expected entry 'contrib/source/Sources' in Release file (Wrong sources.list entry or malformed file)
[/HTML]I need Virtualbox for a few Windows tasks, but if I can't get this working I'll have to go back to double booting... :(
Please help...

---

### Post by Lampi on 2011-12-13
according to [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

the correct entry for oneiric is:

```
deb http://download.virtualbox.org/virtualbox/debian oneiric contrib
```

---

### Post by intruderukr on 2011-12-14
> **Lampi said:**
> according to [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

the correct entry for oneiric is:

```
deb http://download.virtualbox.org/virtualbox/debian oneiric contrib
```
ok, maybe that works.  There were a few PPA's listed on my sources for virtualbox and I deleted them all and added yours. Now my update errors look like this:
W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 360D382BFC695405, W:Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

An issue for another thread of course...thanks so much for your help! :)

---

### Post by jbest on 2012-05-02
I had the same problem. Still haven't directly solved it, but it does work to instead install using:


sudo apt-get install virtualbox-4.1

From the direction at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

This installed the latest version and retained my previous VMs and settings.

---

### Post by ampedlp on 2012-05-08
Oracle doesn't distribute the source code. In Synaptic, go to Settings>Repositories>Other Software and uncheck the (Source Code) entry for virtualbox.org and the "Failed to fetch" message will no longer appear. Also, as I am installing this for the first time, I noticed that there are two entrys for finding Virtualbox in the repositories: "virtualbox" is from the ubuntu repository, where "virtualbox-4.1" is from the virtualbox.org repository. Hope this helps.

---

### Post by CeltaWeb on 2012-06-04
I had the same problem and its true the issue was that when I added the repository to the sources list an additional entry was added with a suffix of source. I just opened up the update manager select **Settings** from the bottom and deleted the entry with the source suffix. 

Then the usual from the terminal.

sudo apt-get update
sudo apt-get install virtualbox-4.1

and it was all smooth sailing no errors! I hope that helps.

---

### Post by horsemanoffaith on 2012-12-01
Thanks for your post ampedlp... this fixed my issue!!!

---

### Post by pamasz on 2013-01-22
> **jbest said:**
> I had the same problem. Still haven't directly solved it, but it does work to instead install using:


sudo apt-get install virtualbox-4.1

From the direction at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

This installed the latest version and retained my previous VMs and settings.
Thanks! that helped me, after some unsuccessful advices...

---

### Post by archery on 2013-01-22
> **pamasz said:**
> Thanks! that helped me, after some unsuccessful advices...


This is an old thread and 4.1 is the old version. Did you follow the instructions here:

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by smehurko.info on 2013-12-29
[SIZE=2][COLOR=#333333][FONT=UbuntuRegular][SIZE=3]The reason is an invalid entry in **/etc/apt/sources.list** file. There is no source package in the VirtualBox source repository. Just remove the deb-src line:[/SIZE]
[/FONT][/COLOR]
```
***sudo nano /etc/apt/sources.list***
```
[COLOR=#333333][FONT=UbuntuRegular]
[SIZE=3]Find and remove(or comment) this line:[/SIZE][/FONT][/COLOR]
```
***deb-src [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid non-free***
```
[SIZE=3]
[/SIZE][/SIZE][COLOR=#333333][FONT=UbuntuRegular]This should solve the case. 
Try to update again.
[/FONT][/COLOR]

---

### Post by oldos2er on 2013-12-29
This thread is quite old, and since the original question is about a version of Ubuntu no longer supported, closed.

---

