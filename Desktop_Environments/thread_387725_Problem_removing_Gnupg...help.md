---
title: "Problem removing Gnupg...help"
date: 2007-03-18
forum: Desktop Environments
---

### Post by lightzoo on 2007-03-18
Hi,

I want to remove the default Gnupg (1.4.3.*) and install v.1.4.7 or v.2.0.3 that I will compile.

My problem is I can't figure out how to ONLY remove Gnupg.  For some reason apt-get is trying to remove all kinds of other apps it should not remove.

Here's what apt-get wants to remove:
---------------
The following packages were automatically installed and are no longer required:
  kontact kubuntu-desktop libkleopatra1 korganizer ubuntu-keyring
  libkpimidentities1 ubuntu-minimal kaddressbook kmailcvt libgpgme11 kmail
  kdepim-wizards gnupg
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gnupg kaddressbook kdepim-wizards kmail kmailcvt kontact korganizer
  kubuntu-desktop libgpgme11 libkleopatra1 libkpimidentities1 ubuntu-keyring
  ubuntu-minimal
-------------------------

Anyone have a suggestion?  

On a side note:

1. Why is the version of Gnupg shipped with Kubuntu not the current stable 1.4.7...but the older and pretty obsolete 1.4.3.*?

2. Is there a apt-get  command to only remove a specific app/package and not the deps?

3. I really like Kubuntu but **I REALLY DISLIKE**  how difficult it can be to remove a package...why is it so difficult?  Why can't I just remove a certain app and not remove all kinds of apps which apt-get thinks are deps but are not really deps?

Regards,

---

