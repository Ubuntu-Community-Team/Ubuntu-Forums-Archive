---
title: "Ubuntu Minimal vs Ubuntu Standard - Security Differences?"
date: 2009-03-08
forum: General Help
---

### Post by ArtF10 on 2009-03-08
What is the difference, in terms of security, between a standard Ubuntu installation(Gnome) and a minimal Ubuntu+Gnome Core installation as described here:  [http://linuxuser.se/~lassekongo83/2008/07/installing-a-minimal-ubuntu-installation/](http://linuxuser.se/~lassekongo83/2008/07/installing-a-minimal-ubuntu-installation/)

I mean, is the standard version more secure than the minimal version which does not install much?

---

### Post by Dr Small on 2009-03-08
Both are built upon the same base, so I would have to say they are both equal in regards to security.

---

### Post by tommcd on 2009-03-08
If we assume that a minimal install will have fewer services running, then a minimal install will be more secure than a full install. Fewer services running (especially ssh and all of the server services) means greater security.

---

### Post by ArtF10 on 2009-03-08
I went here to find out more about what each Ubuntu package does(this is for Intrepid):
[http://packages.ubuntu.com/intrepid/](http://packages.ubuntu.com/intrepid/)

I could NOT find any package with the word "security" in it.  Where do the security packages come from?

---

### Post by tommcd on 2009-03-08
> **ArtF10 said:**
> 
I could NOT find any package with the word "security" in it.  Where do the security packages come from?

The security comes from the kernel itself, and the packages that run on it. Many of the updates that you get are security patches for security vulnerabilities that get discovered.

There are security programs like firewalls (firestarter, guarddog) and rootkit hunters (chkrootkit, rootkit hunter) etc.

---

### Post by ArtF10 on 2009-03-08
> **tommcd said:**
> **The security comes from the kernel itself**, and the packages that run on it. ....

Ah!  That's what I wanted to know.

Thanks.

---

