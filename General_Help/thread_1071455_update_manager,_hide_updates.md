---
title: "update manager, hide updates"
date: 2009-02-16
forum: General Help
---

### Post by Lerxst on 2009-02-16
I had to manually compile and .deb package vnc4server for X64 Intrepid, as the 64-bit version for Ubuntu is broken so copy/paste between hosts doesn't work.

However, Update Manager have ever since insisted that I have an update for vnc4server awaiting installation.

How can I hide this update so it won't show up? I Googled and found one thread saying starting Synaptic, highlighting the package and chose Package ->  Lock version should fix this, but it still shows up in Update Manager.

Is there any other way to fix this?

---

### Post by drs305 on 2009-02-16
Locking the version in synaptic hides the Update Manager update option for me. 

Is the version in synaptic that you locked the same version as the one that shows in update manager? Highlight the package in Update Manager to see the version number that is about to be upgraded. 

When you lock a version in synaptic, an entry is made in /var/lib/synaptic/preferences . I locked *rhythmbox* for this example:
> Package: rhythmbox
Pin: version 0.11.6svn20081008-0ubuntu4.2
Pin-Priority: 1001

You can check to see if there is a lock on the package you are getting the update for. If there isn't, a bit of a hack would be to create an entry in the above file. The *Package* name would be the name that appears in bold in Update Manager and the version number would be the Version number in the window, minus the ending " **:**  " 
**Make a backup copy of the file before you change it. If you manually remove an item from this list you may break synaptic.**

One additional note: This post concerns synaptic and update manager. Although they work together, apt-get and aptitude deal with things a bit differently. If you lock a version in synaptic, it can and will still be updated via terminal with aptitude/apt-get upgrade unless you have placed a *hold* on the package via the command line.

---

### Post by Lerxst on 2009-02-17
> **drs305 said:**
> 

Is the version in synaptic that you locked the same version as the one that shows in update manager? Highlight the package in Update Manager to see the version number that is about to be upgraded. 

It doesn't say. It only says vnc4server, Virtual network computing server software (Size 1.0 MB). The Description tag only describes what vnc is all about and the Changes tab says the list of changes is not available.

Synaptic says the installed version is 4.1.1+Xorg1.0.2-0ubuntu7 and the latest version is 4.1.1+Xorg1.0.2-0ubuntu7.

This is the same version I compiled, by the way. It's from 2005 or so, and I'm quite sure the installed version prior to me compiling and installing the new one, was the same.

> When you lock a version in synaptic, an entry is made in /var/lib/synaptic/preferences .
You can check to see if there is a lock on the package you are getting the update for. 

Yes there is:
[B]
me@localhost:~$ cat /var/lib/synaptic/preferences 
Package: vnc4server
Pin: version 4.1.1+xorg1.0.2-0ubuntu7
Pin-Priority: 1001[/B]

Is there any other way I can fix this?
By the way, I have a .deb package of vnc4server which fixes the broken copy/paste between hosts that's with the 64-bit version of Ubuntu.
I assume the Ubuntu team should at least be interested in including this in their repository. Who can I contact about this?

---

### Post by drs305 on 2009-02-17
If it isn't a typo, this could be the reason:
```

Package: vnc4server
Pin: version 4.1.1+**[COLOR="Red"]x[/COLOR]**org1.0.2-0ubuntu7
Pin-Priority: 1001

```

Make sure the locked version has an upper-case **[COLOR="Red"]X[/COLOR]**

---

### Post by Lerxst on 2009-02-17
> **drs305 said:**
> If it isn't a typo, this could be the reason:
```

Package: vnc4server
Pin: version 4.1.1+**[COLOR="Red"]x[/COLOR]**org1.0.2-0ubuntu7
Pin-Priority: 1001

```

Make sure the locked version has an upper-case **[COLOR="Red"]X[/COLOR]**

No, I'm afraid that was not the reason....

---

