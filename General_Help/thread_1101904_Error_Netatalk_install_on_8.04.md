---
title: "Error Netatalk install on 8.04"
date: 2009-03-20
forum: General Help
---

### Post by dmovad on 2009-03-20
I tried to install netatalk_2.0.3-9_amd64.deb on a duel xeon-64 machine today running 8.04-64 with LTSP and received the following error when executing the "debi" command:

root@server:/usr/src/netatalk/netatalk-2.0.3# debi
Selecting previously deselected package netatalk.
(Reading database ... 118587 files and directories currently installed.)
Unpacking netatalk (from netatalk_2.0.3-9_amd64.deb) ...
Setting up netatalk (2.0.3-9) ...
Starting Netatalk services (this will take a while): nbp_rgstr: Connection timed out
Can't register server:Workstation@*
invoke-rc.d: initscript netatalk, action "start" failed.
dpkg: error processing netatalk (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 netatalk
debi: debpkg -i failed

My install failed and I'd sure appreciate any help that will get me going.  Is there any possibility of issues with LTSP and Netatalk on the same server?

thanks...
Dave

---

