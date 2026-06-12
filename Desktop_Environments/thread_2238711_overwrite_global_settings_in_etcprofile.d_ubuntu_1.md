---
title: "overwrite global settings in /etc/profile.d ubuntu 14.04 gnome flashback"
date: 2014-08-09
forum: Desktop Environments
---

### Post by dieter-erich on 2014-08-09
Hi,
   my server is setup to globally source (from the login shell) various settings in /etc/profile.d/ for all users to run the programs without too much ado.  

However, I need to run a new program suite that brings with it a number of python scripts and libraries that are largely incompatible with the system libraries (e.g. other versions etc. that are specified in the PATH and/or LD_LIBRARY_PATH and thus interfer with proper execution). Therefore I need to overwrite these variables and settings in my login shell without affecting the other users and launch this program form a 'clean system'.

 I understand that I can (re)set the PATH and LD_LIBRARY_PATH from within .bashrc and .profile in my login shell but I do not get rid of the environment variables set on login from the scripts in  /etc/profile.d.

Thus my question: Is there a way to overroule everything specified in /etc/profile.d as if it were not present?

Thanks, D-E

---

