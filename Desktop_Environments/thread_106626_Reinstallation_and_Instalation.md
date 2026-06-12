---
title: "Reinstallation and Instalation"
date: 2005-12-21
forum: Desktop Environments
---

### Post by TuxDaddy on 2005-12-21
To All:

If your like me you have hosed your system a few times.  If you haven't yet then maybe if you ever have to reinstall this could help.

Make sure when you install Ubuntu the 1st time you partition your drive correctly.

1 partiton for /root
1 partition for /home
1 partition for /swap

Why?  If you do this and need to reinstall all you need to do is format and set mount point for /root.  Then set the mount point again for /home (DO NOT FORMAT).  Finally set the mount point for swap (not really nessary, just check in the partitioning setup).

When this is done and you go to reinstall make sure you name your users the same username as your previous installation.  All your data in your home folder and desktop setting will be there.

Hope this helps someone.  I found it out by breaking my system.

R

---

