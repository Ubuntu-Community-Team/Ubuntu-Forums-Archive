---
title: "Accessing Vista file shares in Dell Ubuntu Netbook Remix"
date: 2009-01-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by emnii on 2009-01-08
I'm having a hell of a time getting to my shared files on a Vista64 computer from my new Dell Mini 9 running Dell Ubuntu Netbook Remix. The shares show up in smblist and smb4k but they won't mount in smb4k (with a mount error 2) and they don't show up at all in Nautilus. I'm running no firewalls on either machine. 

Really, all I want is to share my music and videos so if there's an easier way to go about it, I'm all for it. Has anyone else run into this problem?

---

### Post by anjilslaire on 2009-01-09
Yup, I had a problem mapping samba shares that I knew were functional. 

Map the shares by the machine IP. I believe there's an issue in nautilus in mapping via name at the moment.

Go to Places > Connect to Server > 
Server Type: windows share
Server: 192.168.x.x (whatever your Vista IP address is)
Folder Name
enable the Bookmark if desired
click Connect

---

### Post by emnii on 2009-01-09
that worked, thanks for the help!

---

