---
title: "W: GPG Error Message"
date: 2009-02-19
forum: General Help
---

### Post by cheetaux on 2009-02-19
Lately when I run Update Manager I get the following error message:

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

Can someone please explain how to fix the problem?

Thanks

---

### Post by MedianMajik on 2009-02-19
> **cheetaux said:**
> Lately when I run Update Manager I get the following error message: Can someone please explain how to fix the problem?
ThanksFunny, I just asked about the [same thing]("http://ubuntuforums.org/showthread.php?t=1074607") 4 hours ago.  Basically you add repositories from a third party and have to accept a security key as well.  As far as I know it varifies you trust an outside source and won't hold the standard Ubuntu repositories accountable for any problems that arise.

I hope this helps.  Use the instructions I received in my thread and just replace my key with yours.

Like this:
gpg --keyserver keyserver.ubuntu.com --recv 60D11217247D1CFF
gpg --export --armor 60D11217247D1CFF | sudo apt-key add -
sudo apt-get update

Omg you have the exact same problem I had to the "T" with the exact same key, but a different version of Ubuntu

---

### Post by cheetaux on 2009-02-19
MedianMajik,
Thanks, that solved my problem.  

I don't see the "thanks" button any more, did they remove that feature?

---

### Post by forger on 2009-02-20
Fix your ppa link repositories as well:
[thread=1056099]**Update your Launchpad PPA repositories and apt keys**[/thread]

---

### Post by MedianMajik on 2009-02-21
> **cheetaux said:**
> MedianMajik,
Thanks, that solved my problem. I don't see the "thanks" button any more, did they remove that feature?Apparently it has been disabled due to a server upgrade.  You're welcome all the same.

---

