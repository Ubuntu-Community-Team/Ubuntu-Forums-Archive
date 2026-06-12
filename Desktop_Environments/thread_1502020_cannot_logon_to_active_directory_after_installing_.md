---
title: "cannot logon to active directory after installing smbclient"
date: 2010-06-05
forum: Desktop Environments
---

### Post by delineator on 2010-06-05
Hello all,


I am having a problem using smbclient on my Ubuntu 10.04 workstation. I use likewise open5 to authenticate to a windows server 2003 domain controller. I installed the smbclient utility mounted the network drives to the local desktop, then all of a sudden I cannot logon to my active directory domain controller. If any one knows what I am talking about what am I doing wrong?

Do I need to change my smb.conf file?
Or do I need to download another repository or utility?

---

### Post by delineator on 2010-06-05
okay, I did find a fix to this. All I did was use the gnome GUI, selected places, then I selected Connect to Server on the drop down menu, then inputted my credentials to my samba share on my Ubuntu 10.04 server. I wanted it to remember my network drive mount so I just selected remember bookmarks and credentials, then I rebooted my ubuntu desktop and it mounted it as a folder. This is close to what I wanted but I would still want it to mount automatically as a network HDD not just a folder.

---

