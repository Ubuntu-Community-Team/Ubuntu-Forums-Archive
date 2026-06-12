---
title: "Problem with ldap and gnome-volume-manager"
date: 2007-02-15
forum: Desktop Environments
---

### Post by mproto on 2007-02-15
Hey everyone,

i tried to set up authentication of my eft installtion againt our ldap according to the CorporateUbuntu guide ([https://help.ubuntu.com/community/CorporateUbuntu](https://help.ubuntu.com/community/CorporateUbuntu)) which worked fine (with some modifications). 
Now i have to solve two problems before beeing completely happy with ubuntu:

1.  It is necessary to map some groups from ldap to local groups. How is that possible ?
          e.g. user: john (ldap) with groups sysadmin & staff (ldap) -> group admin (local), video (local), plugdev (local)...
          my first idea was to try pam_group but i was not very successfull

2.  after setting up all the libnss and ldap-stuff the gnome-volume-manager doesn't pmount a new device. So if i plug in a new usb-stick there will apear no new icon on my desktop. I already tried to add a new group "nvram" to /etc/group but nothing changed. 

I was wondering if the author of the above guide or anyone of you hasn't had the same problems and solved them ?

Thanks

Michael

---

