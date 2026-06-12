---
title: "Mounted share - where is it mounted??"
date: 2006-06-12
forum: Desktop Environments
---

### Post by gnosis-wi on 2006-06-12
When I go to Places->Network Servers->pathtoshare and right click on a shared directory on another box (a smb share on a CentOS box) I can select "Connect to this Server".  This appears to mount the share and places an icon on my desktop.  The icon works as expected; when I double click it, it opens the share.

My question is, where is this share *actually* mounted?  When I browse my file system, there is no mention of this in /home/username/Desktop.  

If I do a "mount" at the command line, this share does not appear on the list.

What gives?  I need to be able to access the share via my normal file system, not just through GUI.

Thanks,
G

---

### Post by gnosis-wi on 2006-06-12
...just one bump (before I go pester the IRC channel) ;)

---

### Post by scxtt on 2006-06-12
what connection method are you using?  AFAIK, none of them are akin to nfs - where the filesystem is mounted over a network connection ... for instance, i use "connect to server" to connect to my old college account via ssh - it's not 'mounted' anywhere ...

---

