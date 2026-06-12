---
title: "Remote Desktop not working"
date: 2011-03-29
forum: Desktop Environments
---

### Post by b89.smith on 2011-03-29
When I configure my remote desktop preferences I am not able to connect using a VNC client to my ubuntu computer. The password box pops up when I type in the password it says it could not authenticate. I have changed the password in the remote desktop preferences and this has not solved the problem. I tried to find a way to reinstall the remote desktop application on ubuntu, but I cannot find what its name is and reinstalling vncserver did not help.

---

### Post by doctorzeus on 2011-03-29
Null

---

### Post by wyliecoyoteuk on 2011-03-29
vnc in Linux uses  hostname:screenumber

e.g. localbox:0

and the password is the VNC password, not your user password.

---

