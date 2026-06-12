---
title: "How to enable X client connections via tcp?"
date: 2011-04-04
forum: Desktop Environments
---

### Post by DavidBiesack on 2011-04-04
How does one enable tcp X connections for Ubuntu 10.10?

I would like to enable X server connections so that I can open apps freely between my desktop and laptop. ssh -X is already working fine, but for example, I have GNU Emacs already running on one machine and I want to use M-x make-frame-on-display to share the same Emacs across multiple displays.

I've already done :

[INDENT][FONT="Courier New"] mydesktop$ xhost +mylaptop
mydesktop$ xhost +mylaptop.mydomain[/FONT]
[/INDENT]
then on mylaptop (just using xload as an example)

[INDENT][FONT="Courier New"]mylaptop$ xload -display mydesktop.mydomain:0
Error: Can't open display: mydesktop.mydomain:0[/FONT]
[/INDENT]
I Looked [here]("http://ubuntuforums.org/showthread.php?t=1310771") and [here]("http://serverfault.com/questions/99147/karmic-koala-ubuntu-enable-remote-x-clients-through-tcp") (and elsewhere) and tried those proposed solutions, but none seem to work for Ubuntu 10.10. All seem to be geared towards previous releases.

It's not a connection problem (i.e. ssh works fine between the two); it's just the non-ssh X connection that fails.

fyi:

[FONT="Courier New"]mydesktop$ uname -a
Linux d72933.na.sas.com 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 GNU/Linux[/FONT]

---

