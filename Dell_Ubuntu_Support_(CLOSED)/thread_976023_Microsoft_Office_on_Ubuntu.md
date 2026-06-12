---
title: "Microsoft Office on Ubuntu"
date: 2008-11-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by yakker.yak on 2008-11-08
If you need a few applications from Windows that you can't live without (i.e. Microsoft Office, some games, etc.) there are a few ways to install these directly in Ubuntu.

All are based on [Wine](http://www.winehq.org/) (Windows emulation layer).

[CrossOver Linux](http://www.codeweavers.com/products/cxlinux/) & [CrossOver Games](http://www.codeweavers.com/products/cxgames/):
- Easy point-and-click install
- Stable releases/updates to maintain compatibility
- $39 but you support the developers and Wine
- 30-day free trial to test your application(s)
- Comes with support

[Play on Linux](http://www.playonlinux.com/en/download.html):
- Easy point-and-click install
- Community support
- $0

[Wine](http://www.winehq.org/):
- Manual install of applications (e.g. see [install of Microsoft Office](https://help.ubuntu.com/community/Microsoft_Office))
- Community support
- $0

Check out the compatibility lists to see if your application is supported.

If your application is not supported but you still need it, you can always install Windows within Ubuntu via [VirtualBox](http://www.virtualbox.org/) or [VMware](http://www.vmware.com/download/server/) and then install the application directly within Windows running on top of Ubuntu.

Both are free (as in beer) but VirtualBox is also free software (as in freedom).

---

### Post by yakker.yak on 2008-11-08
If you have a Dell Mini, the DEBs for Play On Linux and CrossOver will be built for 386 and not LPIA so they will not work if you're running the Dell version of Ubuntu.

The generic installers should work though:

If you try the 30-day trial for CrossOver Office or CrossOver Games select the Loki installer.

For Play on Linux the generic installer is [here](http://www.playonlinux.com/en/download-generic.html).

Wine should be available in the standard repositories and you should be able to install it like all other software via the package manager.

---

### Post by yakker.yak on 2008-11-11
For Dell's customized Ubuntu, which is built for the i386-compatible, but different LPIA architecture, there is now a new version of the package installer that will enable you to install i386 DEBs without needing to repackage them for LPIA.

Once installed, you should be able to use the default DEB packages for CrossOver and Play on Linux (as opposed to the command-line installers).

The installation details are [here]("http://ubuntuforums.org/showthread.php?t=982260").

---

### Post by yakker.yak on 2008-11-11
The Gdebi installation instructions are [here]("http://ubuntuforums.org/showthread.php?t=982260").

---

### Post by gavinfoxx on 2008-11-12
What is hte best way to install this version of gdebi on the mini 9? I cant seem to get it to install in such a way that the OS completey understands whats going on...

---

### Post by sirebral on 2008-11-12
I thought I would mention Open Office in this thread.  Open Office works with Word Documents and is a great software.

---

### Post by iaskedalice09 on 2008-11-13
> **sirebral said:**
> I thought I would mention Open Office in this thread.  Open Office works with Word Documents and is a great software.
Agreed, I don't use Office at home. OO.org is great software.

---

### Post by n1unqn on 2008-11-13
Yeah Open Office 3 rocks, Office 2007 sux big time on it's user interface, M$ are going down!

---

### Post by iaskedalice09 on 2008-11-14
> **n1unqn said:**
> Yeah Open Office 3 rocks, Office 2007 sux big time on it's user interface, M$ are going down!
World Domination of the Penguins!

---

### Post by inphektion on 2008-11-14
I need outlook 2007 for integration with OCS, unified messaging and various features with shared calendars.  I wish someone could figure out how to make another mapi client.  outlook 2007 only runs in a vm, no crossover, wine, etc gets it running right that I've found so far.

---

### Post by yakker.yak on 2008-11-14
> **inphektion said:**
> I need outlook 2007 for integration with OCS, unified messaging and various features with shared calendars.  I wish someone could figure out how to make another mapi client.  outlook 2007 only runs in a vm, no crossover, wine, etc gets it running right that I've found so far.

Have you tried the latest version of Crossover (7.1.1)? Other users are reporting 'Silver' in terms of compatibility, which is pretty close to everything working as on Windows:

[http://www.codeweavers.com/compatibility/browse/name/?app_id=2841](http://www.codeweavers.com/compatibility/browse/name/?app_id=2841)

---

