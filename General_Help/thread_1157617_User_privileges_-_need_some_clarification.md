---
title: "User privileges - need some clarification"
date: 2009-05-12
forum: General Help
---

### Post by spydeyrch on 2009-05-12
Hey, new to the forum. I have been using ubuntu on and off since 5.04. Ubuntu is what really helped to open the doors to Linux for me and I have been in love with linux ever since!:KS I won't say that I am a pro but I like to dabble here and there. Currently I am having some difficulty understanding a few things. I have a dual boot with Vista 64 SP1 and Ubuntu 9.04 64. It took me a while to get ubuntu 9.04 to install, it wasn't very pretty. :( But that is beside the point.

Here is my issue: I have myself as the initial user and then created a user account for my son. I have installed the education packages for him because he loves to use them; he is 3. I have some other periferals connected to my machine, such as external HDD via firewire. I have tried to play around with the different user privileges under the System -> Users and Groups settings. I don't want him to have acces to certian things, i.e. external hdd, internet connection, and other settings. I realize that for a lot of the changes to take place or to even enter into the menu for that matter, the root password will be needed, which he doensn't know, so that isn't that big of a deal What concerns me is that even though I have the "Acces External Storage Devices Automatically" unchecked, it still automatically mounts and displays the external drive on his desktop, which is what I dont' want. The same holds true for the other privileges: printers, ethernet connections, optical drives, etc. I have added him to the "Users" group and the same things still happens. I have even fooled around with my privileges, which doesn't really do a thing.

So, am I doing something wrong here? How can I make it so that the privileges that I check/uncheck really do/don't allow access to that privilege?

Thanks in advance for you help and patience!! :-)

-Spydey

---

### Post by KhurramM on 2009-05-13
see

man sudoers

this might help u

for examples u need to search the internet

---

### Post by CatKiller on 2009-05-13
Don't forget that you'll need to log out and log back in for group membership to be updated. If you can't get the volumes to not show on the Desktop through permissions, you could go into gconf-editor and uncheck the /apps/nautilus/desktop/volumes_visible key. If he's 3 he's unlikely to be able to reverse this.

---

### Post by spydeyrch on 2009-05-14
Awesome, thanks for the info guys, I appreciate it. :-):p

---

