---
title: "Neworked Computers"
date: 2005-11-24
forum: Desktop Environments
---

### Post by CharlieC on 2005-11-24
I have an XP Home box and a Ubuntu 5.10 box, both connected through a Netgear router.
 Ubuntu can see the XP box and I can actually put something in the XP shared folder without a problem. However when I click on the Ubuntu box in the Network Servers tab, I can see the Ubuntu box, called linuxthree but when I click the icon I am asked for a password. I have put in my password both user and tried root as well. NG.
 Can anyone tell me how to get rid of the password request so that I can move to the next phase which I think is making a share that XP can see.

TIA
Charlie

---

### Post by sabitha on 2005-11-24
create a SMB user, make sure this account exists on your Ubuntu Linux.

Code:

sudo smbpasswd -a `whoami`


and set your password

then

System > Administration > Shared folders

---

### Post by tom-ubuntu on 2005-11-24
You have to use the samba users, have a look here:
[http://ubuntuguide.org/#addeditdeletenetworkusers](http://ubuntuguide.org/#addeditdeletenetworkusers)

---

### Post by CharlieC on 2005-11-24
Thanks, that worked. So wimple when you know how. I saw the commands you recommended but  did not realize that I had to do that.

    I picked my regular user name. I am not sure if that was a bad move. Should I have made up a seperate user?

Thank you very much for the help

Charlie

---

