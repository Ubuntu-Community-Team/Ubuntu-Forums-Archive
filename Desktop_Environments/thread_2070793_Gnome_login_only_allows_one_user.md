---
title: "Gnome login only allows one user"
date: 2012-10-13
forum: Desktop Environments
---

### Post by Zfs on 2012-10-13
Hi
I installed ubuntu64 server and zfs for a large filesharing array. The system is very stable. Added ubuntu-desktop after a few days, but the first installation was interrupted rudely by a rogue network connection. Re-installed apt-get install ubuntu-desktop. 

Problem: I have 6 standard users on the machine, and two superusers ( in the sudo group) and one in the root group. Ever since I installed desktop, only the user in the root group can log in to Gnome. All other users are shown at the gnome login screen, but when I select any one, and type in the user's password, the gui closes and just goes back to login. The password gets accepted but gnome just does not allow any user besides the user in the root group to log in. 

Where do I start looking? There are no obvious groups for x11 or Gnome in/etc/group. Why would gnome reject all normal users?

---

### Post by steeldriver on 2012-10-13
Check that the user's home directories have the correct ownership and permissions - likewise for the /home/*user*/.Xauthority and /home/*user*/.ICEauthority files - otherwise their X sessions won't be able to start

Not sure it's a good idea to have regular users belonging to group root

---

### Post by Zfs on 2012-10-13
I see the second superuser's .Xauthority and .ICEautority files ownership was root:root, while the user that could log in was set to paul:paul.  I fixed it, but can't test until i get back to the office on monday.  

I see the standard users don't have any .Xauthority or .ICEauthority files. Will they be generated automatically or can i create them?

---

