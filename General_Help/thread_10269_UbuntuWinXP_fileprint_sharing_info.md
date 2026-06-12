---
title: "Ubuntu/WinXP file/print sharing info"
date: 2005-01-06
forum: General Help
---

### Post by pmshoop on 2005-01-06
Hey all, 

I finally got all the bugs worked out of file/print sharing for WinXP and Ubuntu.

Steps....

Install Samba and set as per instructions in the 'unofficial Ubuntu 4.10' at the following address 
[http://ubuntuguide.org/](http://ubuntuguide.org/)

THEN in Win XP make sure you can see the files on your Unix Box that you set up to share.  If you can, proceed.  If not, got back and re-setup Samba and / networking in Ubuntu.

GOTO> Control Panel > Add Remove Programs > Add Remove Windows Components:

Add ALL the networking items that are currently not installed.  Mainly you need to install the Peer-to-Peer support item but throw them all in for good measure.  Never hurts right...

Next, goto your Ubuntu box and pull up the network.  You should now be able to see and access the files on your windows box that are shared.  You will be prompted for  a username domain and passwd.  My wifes WinXP laptop only had a username.  I left the other feilds blank.  Works good.

Hope this helps.

Paul.

P.S. to print share (to WinXP or From win XP).  In Win XP search for the printer being shared on your Ubuntu box.  Right Click it.  Click Connect.  Install any drivers prompted if nessecary.  And visa versa for Ubuntu.  Easy as pie... any questions feel free to ask.   :-k

---

### Post by valter on 2005-03-11
Thanx it helped, but I dont see any printers from ubuntu box, that are shared from win xp and sometimes my ubuntu shared folder is acsessable, sometimes not. ?

---

