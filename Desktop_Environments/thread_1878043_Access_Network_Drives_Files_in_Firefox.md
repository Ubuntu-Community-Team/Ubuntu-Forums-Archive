---
title: "Access Network Drives Files in Firefox"
date: 2011-11-09
forum: Desktop Environments
---

### Post by baditaflorin on 2011-11-09
The bug it`s very simple. From the browser, I click upload photo, or maybe Manage Attachment like in this forum, and i want to find a picture to upload from another computer in the network. It`s impossible to do this because i cannot found the network from within the browser.

And the new way to report a bug i find it very stupid , when i want to report a visual problem like this, i don`t know wnat PID it has, it does not matter.
It`s a firefox/ google crome prob;lem no because the bworsing part it`s handled by ubuntu. So it`s a ubuntu problem. And how should i know with pid is the problem.

It`s making me more and more not wanting to report some bugs, because it`s imposible to explain what i want to say.

---

### Post by bluexrider on 2011-11-09
People could help if you gave more info:

Distro?
Browser?
Is this related to network connectivity?
Is it a samba issue?

Give some strong details instead of generalities.

Would be glad to help

---

### Post by baditaflorin on 2012-05-10
> **bluexrider said:**
> People could help if you gave more info:

Distro?
Browser?
Is this related to network connectivity?
Is it a samba issue?

Give some strong details instead of generalities.

Would be glad to help

It`s about this bug [https://answers.launchpad.net/ubuntu/+source/firefox-3.0/+question/2194](https://answers.launchpad.net/ubuntu/+source/firefox-3.0/+question/2194)

That still persist in Ubuntu 12.04 

I know that there are workaround, make some kind of a start up file that load some sutff to gfs or gvs or whats the name of the something that handles mounted shares, but it`s just too complicated for the end user that just need to go to another computer, find a picture that we have there, and upload to facebook, or whatever there need is.

LATER EDIT: This bug was first reported in 2006 !

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/31471](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/31471)

---

### Post by LewisTM on 2012-05-10
The idea of users mounting network shares on-the-fly is relatively new to Linux and hasn't permeated all layers of the user interface.

Traditionally a Linux system administrator would setup mounting of network shares at boot time in the file system tree. Users would then access those directories for which they had permission. It's still the most efficient way to deal with network shares on a home network. Mountmanager is a nice graphical program that has a plugin to mount SMB and NFS shares at startup. 

From the mounted share (say /net/desktop1) you can create symlinks to various important folders and place them in your home folder for easy access. For example a symlink to /net/desktop1/Pictures can be placed in your home and renamed 'Mom's pictures'. This allows you to transparently access those files from any program.

Hope this helps a bit.

---

