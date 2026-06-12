---
title: "Username does not show in login-screen (Lubuntu LXDE)"
date: 2012-10-14
forum: Desktop Environments
---

### Post by mdeterink on 2012-10-14
Hello readers,

I use NFS to connect to an NFS share on my iMac from my Lubuntu netbook. Initially I could not connect to the NFS share on my iMac. I found the answer in changing my UID in Lubuntu from 1000 to 501 (so now these are equal on both my iMac and my Lubuntu netbook for the same user).

But when I log-in to Lubuntu LXDE my username does not show up anymore in the list of users. Does anyone know how I can put it back there? It is not a big issue, but it would be nice if I could put it back.

Thank's in advance,
Marco

---

### Post by Rex Bouwense on 2012-10-14
Not sure if I understand what you are asking.  Can you still log in? Can you still use sudo in the terminal?

Also this site may help
[http://lxlinux.com/#12](http://lxlinux.com/#12)

---

### Post by Cheesemill on 2012-10-14
You could always change your UID back to 1000 and then alter it on the Mac instead.


LXDM (the login manager) only displays names for normal (non-system) user accounts.
By definition these are accounts that have a UID of 1000 or higher.

There is meant to be a way of adding users to this list, just edit /etc/lxdm/default.conf and add your username to the 'white=' line.
However last time I tried this there was a bug in LXDM that prevented this setting from taking effect, I'm not sure if it has been fixed yet.

---

### Post by sidzen on 2012-10-14
Thank you, Cheesemill, for the informative post! 
I hope LXDM is fixed, in this regard.

---

### Post by mdeterink on 2012-10-15
@Cheesmill, thank you very much for your helpful reply! I will try to add my username to the 'white=' line in /etc/lxdm/default.conf tonight. Otherwise, it is no big deal because I am always able to login (to type my username).
The reason why I did not thange the UID on my Mac is that I am not an experienced Linux/OS X command line user or sysadmin. My Mac is my main work station on which I do not want to take any risks.

---

