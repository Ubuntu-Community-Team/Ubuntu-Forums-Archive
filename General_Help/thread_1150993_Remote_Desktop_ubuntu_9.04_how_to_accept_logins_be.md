---
title: "Remote Desktop ubuntu 9.04 how to accept logins before console logon"
date: 2009-05-06
forum: General Help
---

### Post by jasonjm2008 on 2009-05-06
Hey all, a long time windows user here messing with ubuntu, gonna be setting them up with ESXI with 20 workstations per  physical server.

I got the remote desktop logins working to my ubuntu 9.04 workstation working over the internet from my windows vista machine very quickly, maybe 3 mins, done deal, easy as pie

only one problem....

when i reboot the ubuntu 9.04 workstation, I have to login on the ubuntu console before it will accept new remote desktop connections.... which kind of defeats the whole purpose if i need to do a console login first

after the console login, the ubuntu workstation accepts incoming VNC connections no problems...

where did I go wrong?

on a side note how would i change the ubuntu 9.04 listening port for remote connections?

thx all

---

### Post by dopegroove on 2009-06-27
You can make Ubuntu logon automatically to get past this issue. It's not as secure as having the second logon but it works.

[http://www.watchingthenet.com/how-to-enable-automati-logon-in-ubuntu-or-kubuntu.html](http://www.watchingthenet.com/how-to-enable-automati-logon-in-ubuntu-or-kubuntu.html)

---

