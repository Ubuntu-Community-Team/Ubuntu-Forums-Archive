---
title: "Package Installs"
date: 2009-06-10
forum: General Help
---

### Post by OldManRiver on 2009-06-10
All,

Have a post at:

[http://ubuntuforums.org/showthread.php?t=1133527&page=2](http://ubuntuforums.org/showthread.php?t=1133527&page=2)

but topic seems to intimidate people.

Real and current problem is I can not get mkisofs nor isomaster to install on my box.

When I use synaptic package manager, I get errors and installs abort, so I found and downloaded the .deb installer files, but they give me "not supported version" errors and abort.

Can anyone help me get these utilities installed?

OMR

---

### Post by michy99 on 2009-06-10
If you post the errors that you are getting from Synaptic, we may be able to fix it.

---

### Post by OldManRiver on 2009-06-12
M,

Synaptic message is to replace mkisofs with genisofs.

System is not online right now so looking for .deb of this to install.

OMR

---

### Post by synapsys on 2009-06-12
Have you tried using apt-get from terminal or only from synaptic? If not, try installing using apt-get from terminal.... maybe we will get more of an idea of what's going on from the command output.

---

### Post by OldManRiver on 2009-06-15
All,

Cleared this over the week-end with help from the guys at:

irc.freenode#ubuntu

Turns out my status file at:

/var/lib/dpkg/status

was corrupted.  When I got it cleaned up the:

apt-get upgrade and the app installs ran, so have both ISOMATER and genisofs (replaces mkisofs on U) out there now.

Thanks!

OMR

---

