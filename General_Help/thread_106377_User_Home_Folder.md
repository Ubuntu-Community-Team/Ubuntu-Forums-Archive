---
title: "User Home Folder"
date: 2005-12-20
forum: General Help
---

### Post by TomB on 2005-12-20
When remastering the LiveCD there is no home for the user "ubuntu" when chroot'd can I create this folder and change ownership to ubuntu.  Then be able to put hidden files such as fluxbox styles, firefox preferences, and other user specific files?  Or is there another proccess I should follow?

---

### Post by aysiu on 2005-12-20
There's no /home folder for Ubuntu? Are you sure?

---

### Post by TomB on 2005-12-20
When I have uncompressed the filesystem then chroot'd I go into /home and ls and there are no folders for anyone, I know the default user on the the LiveCD is ubuntu, so I wondered if creating this home folder would work.

TomB

---

### Post by aysiu on 2005-12-20
I'm sorry, but what's this chroot stuff?

---

### Post by Gandalf on 2005-12-20
I think it would work as ubuntu will not overwrite already existing folder, but i don't know if it will overwrite firefox preferences though

---

### Post by TomB on 2005-12-21
I missed the bit that says put stuff for the home dir in /etc/skel :)

---

