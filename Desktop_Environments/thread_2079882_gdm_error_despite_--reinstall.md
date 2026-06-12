---
title: "gdm error despite --reinstall"
date: 2012-11-02
forum: Desktop Environments
---

### Post by haleleonj on 2012-11-02
I'm posting this as a solution in case others have the same problem. I have found Ubuntu's sites very useful. I have used them to fix my sound, Unity's panels, and more. I was unable to use the current documentation to fix my gdm problem. 

After uninstalling kdm and kde in general, gdm no longer worked even though I chose it using ```
dpkg reconfigure
``` and then reinstalled it using ```
apt-get install --reinstall gdm
``` :(

I found that /etc/gdm/gdm.conf was supposed to exist and that this file holds gdm configuration information. That file was missing and in place of it seemed to be /etc/gdm/custom.conf. So I deleted it, rebooted and now my system works like I want it too with gdm and everything!:guitar:

I figured it might work because Ubuntu seems to fill in blank files with default files. That didn't happen but the defaults kicked in nonetheless. Thank you to the Ubuntu team for having awesome documentation. Keep up the good work.

---

