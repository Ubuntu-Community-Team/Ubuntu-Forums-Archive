---
title: "Ltmodem and modprobe.conf"
date: 2005-01-09
forum: General Help
---

### Post by drew3 on 2005-01-09
I have a ltmodem which I am trying to get working on Ubuntu. I have built the modules and placed them in the correct place but cannot find modprobe.conf and modprobe.preload to add the neeeded commands. Can anyone point me to where these files are please? :-k 

Thanks
Andrew

---

### Post by graham on 2005-01-10
Hi. I'm in a similar situation at the moment. I've been doing a bit of reading/searching on the forum and have discovered a few posts that discuss the lack of a modprobe.conf file, but nothing concrete to say that I really shouldn't have one as yet. The modprobe.conf man page indicates it should exist, but the fact that update-modules doesn't create leads me to suspect that it's not the case.
 
 At the moment I'm running "sudo ./autoload" from within the ltmodem source directory every time I boot up, but I'm not going to put up with that for much longer.
 
 I saw a suggestion that indicated that option and alias commands could go in /etc/modules, which is used at boot up. I've added the contents of /etc/modprobe.d/ltmodem to it (minus the line that is useful if you've got devfs) and will see if that sorts it out the next time I boot. I'm not optimistic, but will report back here when I've got everything sorted.
 
 Perhaps I should try the build_deb script and see what that produces...

---

### Post by graham on 2005-01-10
As expected, it didn't work. I think I'll look into hotplug next.

---

### Post by az on 2005-01-10
"Perhaps I should try the build_deb script and see what that produces..."

The kernel-package package is not working properly and is not compatible withthe build-deb option.  It will be fixed...

---

### Post by graham on 2005-02-13
[QUOTE=drew3]I have a ltmodem which I am trying to get working on Ubuntu. I have built the modules and placed them in the correct place but cannot find modprobe.conf and modprobe.preload to add the neeeded commands. Can anyone point me to where these files are please? :-k 
  
  Thanks
  Andrew[/QUOTE]
  
  I finally got round to sitting down and trying to sort this out. I got it going with udev. See post 23 of this thread:
  
 [http://www.ubuntuforums.org/showthread.php?t=12813](http://www.ubuntuforums.org/showthread.php?t=12813)

---

