---
title: "SyNAPTIC CRASH from vnc into 2nd ubuntu session"
date: 2011-03-24
forum: Desktop Environments
---

### Post by bwanaaa on 2011-03-24
1)boot ubuntu 10.10-standard desktop edition with the following addons installed: opensshserver, tightvncserver
2)log in as standard user 
3)prefs->remote desktop ->allowed
4)from windows7 pc, ultravnc 1.095 viewer to ubuntu connects well
5)windows putty to ubuntu box, log in as admin
6)in putty,start tightvncserver with tightvncserver -httpport 8081 :1
7)from windows7 pc, ultravnc with ipaddress:1

this starts a vnc window on the windows box containing a view onto the ubuntu box's admin session

OK so far

start synaptic package manager
mark something for removal (like an old version of ubuntu still on the machine!) 
the little red x appears in the checkbox and then synaptic crashes


normal?

this also happens when you try to do anything in this session-for example, upgrade firefox. is it because the another session (the user one) is still operating?

---

