---
title: "Script using gconftool-2 over different users"
date: 2011-12-27
forum: Desktop Environments
---

### Post by rjvencken on 2011-12-27
I'd like to check and alter settings with gconftool-2 But with a single script for different users I tried switching to another user and then applying the tool:
+++++++++++++++++++++++++++++++++++++++
rjv@rjv02:~$ su test04
Password: 
test04@rjv02:/home/rjv$ gconftool-2 --set /desktop/gnome/background/picture_filename --type string /usr/share/backgrounds/InthedarkRedux.jpg

Error setting value: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
test04@rjv02:/home/rjv$ 
+++++++++++++++++++++++++++++++++++++++

Apparently I need to be in the same user Gnome session for this to work. Any way around this?

---

