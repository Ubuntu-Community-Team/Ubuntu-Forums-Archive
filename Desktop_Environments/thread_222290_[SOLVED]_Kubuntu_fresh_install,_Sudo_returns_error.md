---
title: "[SOLVED] Kubuntu fresh install, Sudo returns errors when run by adept"
date: 2006-07-24
forum: Desktop Environments
---

### Post by Co.Sinecure on 2006-07-24
Hi,

I just installed a fresh copy of Kubuntu 6.06 LTS after using the live CD and a persistent USB drive for a week or so.

Whenever I try to run adept, it either informs me "Sudo returned with an error", or if the sudo dialog comes up it says "Conversation with sudo failed".

sudo works via the command line, and I can run 'sudo adept' without a problem. I had a look at the sudo package, and the final two lines read:
 conflict: sudo-ldap
 replaces: sudo-ldap

The two arrows on the left are greyed-out also.

I have tried re-installing the sudo package but that hasn't fixed it, and I can't seem to find anything regarding the sudo-ldap package using apt-cache search.

Any suggestions?

---

### Post by Co.Sinecure on 2006-07-24
Also I just tried running an shell script installer for a program that I need for work, and got the following message:

 sudo: timestamp too far in the future: Jul 26 00:24:06 2006

(It is now 10:28 am Jul 25)

I found the sudo-ldap package when I enabled the extra repositories (backports, multiverse etc), attempted to install it and uninstall sudo (with the plan to upgrade sudo as the next step), but changes would not commit.

Please help, I want to be able to use kubuntu at work!

---

### Post by Co.Sinecure on 2006-07-24
Well...the timestamp issue is resloved with sudo -K 
I think perhaps it was due to my clock being messed up during the install..

However, adept is still returning the sudo error.

---

