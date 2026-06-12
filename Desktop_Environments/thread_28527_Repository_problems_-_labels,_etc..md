---
title: "Repository problems - labels, etc."
date: 2005-04-20
forum: Desktop Environments
---

### Post by GTKpower on 2005-04-20
I;ve been trying to read up on this, but to no vail.  I know I'm supposed to have all the repositories I need, already available through Synaptic.  But some of them don;t load fully, and I find the "multiverse' "universe" "restricted" labels confusing. 

I have these repositories already added, with certain captions beneath them:

**CD Ubuntu 5.04 "Hoary Hedgehog"  (binary)**
-Officially supported
-Restricted copyright

**Ubuntu 5.04 Updates (binary)**
-Officially supported
-Restricted copyright
-Community maintained (Universe)
-Non-free (Multiverse)

**Ubuntu 5.04 "Hoary Hedgehog" (binary)**
-Community maintained (universe)
-Officially supported
-Restricted copyright
-Non-free (Multiverse)

**Ubuntu 5.04 Security Updates (binary)**
-Community maintained (Universe)
-Officially supported
-Restricted copyright
-Non-free (Multiverse)

Ok, so there they are, as I see them in my list.  Does that look right?  I'm looking for the latest, greatest updates and new apps.  For instance, I couldn't download gnomebaker or graveman.  I got the following error mesage:

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

I must be doing something wrong, no?  :???:

---

### Post by Fab on 2005-04-20
> **GTKpower]I said:**
> http://archive.ubuntu.com[/url] hoary/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

I must be doing something wrong, no?  :???:
 apt-get update after changing sources.list
it basically says it cant find the cached package list on your comp

---

### Post by GTKpower on 2005-04-20
Thanks for trying to help, but it doesn't work.  Apt-get update return the same error code.

---

### Post by GTKpower on 2005-04-21
I fixed it.  My connection protocol was very inefficient.  I downloaded GNOME-PPP from the repositories and connected with that, and that fixed everything.

Thanks for the help!

---

