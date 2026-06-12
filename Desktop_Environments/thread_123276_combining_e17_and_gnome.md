---
title: "combining e17 and gnome"
date: 2006-01-29
forum: Desktop Environments
---

### Post by oceanelement on 2006-01-29
Hello everyone,

a little while ago on ubuntu hoary there was a howto posted by poofyhairguy explaining the process of making e17 and gnome work simultaneously. the same process (given below) does not work with the breezy version. 

=======================================
Then this:

Quote:
sudo gedit ~/.gnome2/session

Look for this line:

Quote:


Change the like to look like this:

Quote:
1,RestartCommand=gnome-wm --default-wm enlightenment --sm-client-id default1
=======================================

A few things that have changed in the ~/.gnome2/session directory are 

1,RestartCommand=gnome-wm --sm-client-id default1  

is now

0,RestartCommand=gnome-wm --sm-client-id default0

I tried the howto method with this line instead with no luck either. 

would anyone know how this can be done with the current version of e17 and breezy? 

oceanelement

---

