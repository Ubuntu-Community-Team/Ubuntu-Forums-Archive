---
title: "Install problems with ubuntu -vmware"
date: 2005-12-03
forum: Desktop Environments
---

### Post by Majin_Buu on 2005-12-03
Hi im not sure if this is in the right section.

Anyways i tried to use vmware workstation by:

First unpacking it (tar)
[B]
tar xvzf VMware.Workstation-5.0.0.Linux.tar.gz[/B]

Then the process started, after it was done I proceeded to:

_bin  doc  etc  FILES  installer  lib  man  vmware-install.pl_
[B]spita@blablablablaabl/Desktop/vmware-distrib$ sudo ./vmware-install.pl
Password:
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/home/terminator/Desktop/vmware-uninstall.pl.

Failure

Execution aborted.[/B]

Ok ???? how the hell (sorry) can it complain about vmware already being installed by tar? I unpacked it.. like i've done with evry other application followed by the standard ./xxx.pl

Sorry if this is in the wrong place, it's 4 am here and I've been trying to solve this error for 2 hours :/

---

### Post by cyb3rj on 2007-12-26
Just because I like finding answers along with questions...

I was having this problem installing vmware-server, and resolved it by
1) making sure there were no vmware pacakges installed
2) removing /etc/vmware

Hope that helps anyone else in their future search for answers.

---

### Post by bharadwaj on 2007-12-26
oh yes this was what happened to me for the first time and i could solve it by just like cyb3rj has replied you but once i had to unisntall 
> sudo /usr/bin/vmware-uninstall.pl
and restart the whole installation process

---

