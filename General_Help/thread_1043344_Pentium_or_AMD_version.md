---
title: "Pentium or AMD version?"
date: 2009-01-18
forum: General Help
---

### Post by rroze002 on 2009-01-18
Hi all,

The other day I installed Ubuntu 8.10 64b version, and most of the systems seem to be working.  But upon trying to install the Flash Player plugin for FireFox, I realized, through trial and error, that I've actually installed the AMD version on my pentium machine.  Is there an option for the 64b version of Ubuntu designated for Pentium architecture, or is this it?  I don't recall having the option for either or:confused:.  If I just leave everything as is, will that cause any problems later on?

Thanks.

---

### Post by oldos2er on 2009-01-18
The 'amd64' version will run on either Intel or AMD 64-bit capable processors; it's only called 'amd64' because AMD was the first to offer 64-bit.

---

### Post by taurus on 2009-01-18
The x86_64 version works for both archs.  It's the same as the x86 version runs on both AMD & Intel.

The problem you have is the flash plugin.  There is a beta version for 64bit though.

---

### Post by jespdj on 2009-01-18
There is no problem with Flash on 64-bit. The 32-bit version of Flash works normally on 64-bit Ubuntu (if you install it, you automatically get nspluginwrapper which is an adapter to make 32-bit Flash work on 64-bit Firefox).

Install the package **flashplugin-nonfree** with Synaptic or in a terminal window:
```
sudo apt-get install flashplugin-nonfree
```
(There is a beta-version of a 64-bit native Flash plugin, but the 32-bit version in the Ubuntu repository also works).

---

