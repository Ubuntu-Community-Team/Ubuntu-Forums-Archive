---
title: "hp printer problems"
date: 2006-03-14
forum: Desktop Environments
---

### Post by RightCoast on 2006-03-14
for some reason for the life of me i can not hook up my hp officejet 7200 series (officejet 7210xi) printer. the printer was set up through a windows 2000nt computer (which would kind of make it the printer's admin??), and it's hooked up to all my computer via LAN. i can't find the uri or anything to set it up using the 'administration>printing' funciton, and it did not auto-detect it on the LAN. help please... i'm out of ideas. :cry:

---

### Post by Koybe on 2006-03-14
The printer on the windows 2000 should have a share name. Grab it.

Then trys using the printer trough samba share and use //host/sharename.

---

### Post by RightCoast on 2006-03-14
i tried to look for the sharename, but could not find anything, is there anyway that i can look up the uri for the printer, or auto-detect it through the network?

---

### Post by Koybe on 2006-03-14
If you browse your windows network you should find it. You can open a nautilus windows, type control+L then smb://hostname or smb://ip_address.

There you can browse.

Another way is to :
smbclient -L host -U user to show the share for one host, but then you need the smbclient package.

---

