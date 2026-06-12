---
title: "AWN Install went bad; Ubuntu won't update"
date: 2007-06-28
forum: Desktop Effects &amp; Customization
---

### Post by vileS on 2007-06-28
Pretty complicated problem.  Wanted to customize my system with AWN (Avant Window Navigator).  Went through Add/Remove program, found Avant, downloaded it, and ran it after the update was completed.

When trying to open the properties for the toolbar, the options window would not display.  I decided to uninstall it, and planned a reinstall later, thinking I missed a manager install or something.


A week later, I decided to reinstall AWN, and got an error message:
*[INDENT]"A error occured, please run Package Manager from the right-click menu or apt-get on a terminal to see what is wrong.  The error message was: 'Error: BrokenCount < 0'"[/INDENT]*

Opened Synaptic Package Manger, and got this error:
*[INDENT]"You have 1 broken package on your system!   Use the 'Broken' filter to locate it."[/INDENT]*


After selecting Edit -> Fix Broken Packages, I get this message:
*[INDENT]"Successfully Fixed Dependency Problems"[/INDENT]*


After clicking Apply, I get this message:
[I][INDENT]"An Error has Occured

The following details are provided:

E: /var/cache/apt/archives/libawn-svn_0.1.2-svn204_i386.deb: trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn0"[/INDENT][/I]

-----

This is sort of where I'm stuck at.  The Update Manager gives an Icon like it has updates available, but gives me an error message that says "It is impossible to install or remove any software.  Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

Running "sudo apt-get install -f" gives me this error:
[I][INDENT]"Unpacking libawn-svn (from .../libawn-svn_0.1.2-svn204_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libawn-svn_0.1.2-svn204_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn0
Errors were encountered while processing:
 /var/cache/apt/archives/libawn-svn_0.1.2-svn204_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)"[/INDENT][/I]

---

### Post by vileS on 2007-06-29
Updated:  Didn't know there was a difference between "Fix Broken Packages" and a Broken Filter.   Removed AWN entirely using Synaptic.  Everything seems fine.

---

### Post by andrewsomething on 2007-06-29
```
"Unpacking libawn-svn (from .../libawn-svn_0.1.2-svn204_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libawn-svn_0.1.2-svn204_i386.deb (--unpack):
trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn0
Errors were encountered while processing:
/var/cache/apt/archives/libawn-svn_0.1.2-svn204_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)"
```

I've actually run into this issue before, it's never broken apt/Synaptic completely for me though, just AWN updates and installs.

Your problem lies in the fact that you have two versions of AWN in your repos that have two different naming systems. 

You seem to have Reacocard's AWN repo and Trevino's eye candy repo both in you source list. It's not a problem, but can cause issues if you try to install one while the other is installed. 

Reacocard's is named Avant-Window-Navigator-svn and depends on libawnsvn.
Trevino's is named Avant-Window-Navigator and depends on libawn0.

libawnsvn and libawn0 will conflict.

You just need to be sure to uninstall one version prior to installing the other. 

I recommend Reacocard's Avant-Window-Navigator-svn as it seems to get updated a bit more often and he seems more involved in the AWN community. (Although Trevino's work providing Compiz/Fusion has been awesome.)

---

