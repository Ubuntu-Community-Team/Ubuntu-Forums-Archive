---
title: "apt-get upgraded. E17 terminally SEGV'd till total reinstall"
date: 2013-01-07
forum: Desktop Environments
---

### Post by jtwdyp on 2013-01-07
I did an ```
apt-get update
apt-get upgrade 
``` yesterday. My "Precise" (LTS) installation was a bit overdue for it {The last time was a little before Thanksgiving...} So I wasn't surprised that E17 from the ppa:hannes-janetzek/enlightenment-svn repo, had some of it's packages updated. Especially since E17 has actually had a release, and one by one most every distro I use has updated to an advanced enough image that I've been having to recreate all my user preference settings due to new file formats or some such... 

Anyway the upgrade seemed to progress normally. It mentioned that it wasn't upgrading the kernel, so when it was done I implicitly installed the new kernel. Again no errors. But when I rebooted to load the new kernel E17 wasn't functional. (I should perhaps mention that I run apt-get from  a virtual console (usually tty1 just to make sure that the process can complete even if something breaks X...) Anyway after the reboot, every time I tried to start my window manager of choice {E17} I got reoccurring SEGV'd errors that simply wouldn't stop... I tried deleting my entire existing ~/.e dir tree, but it still SEGV'd... My Ubuntu was originally installed as an Xubuntu system. But xfce {which I only use as an emergency backup for E} also failed to start properly. except it never gave me an error, it simply seized up with a black screen. (it's times like this that makes me wish I knew of a precise compatible repo that had the classic e16 package as that would be my preferred back-up WM if I could get it...

My solution was to do an ```
apt-cache search e17 > ~/ebad
``` from a root shell.  Then as an after thought I added an ```
apt-cache search enlightenment > ~/ebad
``` Then I edited ebad until it contained only the packagenames, deleting any that weren't exclusive to e. Next I did an ```
apt-get remove $(cat ~/ebad)
``` followed by an ```
apt-get autoremove
```

Then I reinstalled a fresh copy of e17, and some extra emodules... And it works again...  Of course I had to use only new updated themes and recreate all my user settings.  But E17 is working. And seems to be about as up to date as my bodhi installation...  

[B]I guess this isn't so much a help request as a report of what happened, and what worked, in case it might help somebody else...

[COLOR="Blue"]Though if anybody knows about a precise compatible repo with E16 I'd very much like to hear about it???
[/COLOR][/B]
-- 
JtWdyP

---

