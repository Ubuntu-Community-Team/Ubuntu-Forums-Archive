---
title: "failed to initialize core devices: HELP"
date: 2006-06-30
forum: Desktop Environments
---

### Post by outofnicks on 2006-06-30
RESOLVED, see 2nd post.

Still running Breezy, waiting for the CDs in the mail for Dapper. 
I guess it was Gnome that unexpectedly crashed about a week ago, it just froze up for no apparent reason-- I had to do a hard shutdown and I could only boot back into the shell.

I'm now booted into Vector Linux on another partition, and have my Ubuntu partition mounted but don't have permission to read some of the pertinent log files inside /var.

var/log/gdm/:0.log seems pertinent enough, and the only one I can view besides /var/log/Xorg.0.log, which is pretty long but I can post parts of that if needed. 

Can someone point me in the right direction on what to do here, I really want to get back into Ubuntu! Here's /var/log/gdm/:0.log:
> X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jun 24 16:40:22 2006
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(EE) xf86OpenSerial: Cannot open device /dev/input/mice
	No such file or directory.
(EE) Configured Mouse: cannot open input device
(EE) PreInit failed for input device "Configured Mouse"
No core pointer

Fatal server error:
failed to initialize core devices


---

### Post by outofnicks on 2006-07-01
I tried the sudo dpkg-reconfigure xserver-xorg trick, but that didn't help. Something was really screwed up and I never found out what it was--fortunately, I had a backup.tgz file that was made a couple months ago using a tutorial from the how-to section, and restored my system from that. Lost the updates made since that was made, but at least I'm back in the swing :)

---

