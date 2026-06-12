---
title: "NFS File Sharing Troubles"
date: 2008-01-21
forum: Desktop Environments
---

### Post by elevenfifty5 on 2008-01-21
Recently (About an hour ago) I right clicked my public folder (Downloads and IM file transfers go here) and I selected share this folder. Ubuntu graciously did all the work and set up (from what I have gleaned) a bunch of different daemons (sunrpc samba-netbios and a few other things) I however have had a very quick change of heart as now I wish to undo this. I googled for a while but really found nothing helpful. Is there any way I can completely undo this (I am talking directories configs services and all.) I am still pretty novice. I would like to undo this without reinstalling gutsy. (Which wouldn't hurt to bad considering my partition scheme)

Any help would be most appreciated.

---

### Post by AndyCooll on 2008-01-21
If you right click on the shared folder there is an option "Sharing Options", you can untick any shares. You could also look in System > Administration > Shared Folders and if it's displayed there then remove it.

:cool:

---

### Post by jamzen on 2008-01-21
Were you sharing with NFS or with Samba?
[1]  If there's a file /etc/exports, and it lists the path of your exported directory, then you're sharing with NFS;
[2]  If the last 50 lines or so of /etc/samba/smb.conf contain a reference to the directory you shared, then you're sharing with samba.

If [1], then deleting /etc/exports will stop the sharing;
If [2], then deleting the sharing lines at the end of /etc/samba/smb.conf will stop the sharing.

Of course you will read the manpages for "exports" or for "smb.conf" before you proceed, right?

Finally, if you really want to uninstall the NFS or Samba packages themselves, use System->Administration->Synaptic.  That seems a little drastic.

You could leave the service packages for NFS and Samba installed, but prevent them from starting at boot time, by invoking System->Administration->Services; scroll down to the "Folder sharing service" entries and uncheck the ones you don't want running.  There are (guess what) two entries: one for NFS and one for Samba.

Hope this helps.

---

### Post by elevenfifty5 on 2008-01-21
For the most part that is what I did before posting, I viewed this forum post as a last resort. I just noted that it opened a bunch of ports and such even while the folder wasn't being shared.

---

