---
title: "where does ubuntu store shared folders (not in smb.conf!)"
date: 2008-06-19
forum: Desktop Environments
---

### Post by edoardo on 2008-06-19
Ubuntu 8.04 desktop
I have some folders shared via samba. 
They have been set up via right click on the folders in nautilus and using the 'Sharing Options' menu.

I am astonished not to find them in /etc/samba/smb.conf
and even could not find them by doing a find . -exec grep ... in the whole /etc

however these shares are persisted across reboots.
so where the heck is ubuntu saving the shares info ???

---

### Post by edoardo on 2008-06-19
it's  /var/lib/samba/usershares

---

### Post by travelinrob on 2009-08-07
Thank you.

---

