---
title: "[SOLVED] NX Client fails to connect"
date: 2008-01-26
forum: Desktop Environments
---

### Post by Moonwings on 2008-01-26
I've installed the NX server on my ubuntu 7.10 laptop and the client on my windows xp machine (downloaded from nomachine).
The install had no errors.
However I get the following error when attempting to connect from windows to ubuntu. It says:
> 
NX> 505 ERROR: Error occurred: public key authentication failed.
NX> 505 ERROR: NX server was unable to login as user: debbie.
NX> 505 ERROR: There is no public key on node 127.0.0.1.
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: 55F4E84E. To get detailed information about
NX> 595 ERROR: the error search for the string 55F4E84E in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 999 Bye.
NX> 280 Exiting on signal: 15

as suggested in several posts, i've also done the following:
> Load up your /etc/ssh/sshd_config file into an editor:

Add the following line & save the file
AuthorizedKeysFile /usr/NX/home/nx/.ssh/authorized_keys2

Restart sshd by typing:
sudo /etc/init.d/ssh restart

i have verified that /usr/NX/home/nx/.ssh/authorized_keys2 does,in fact exist (and contains a key)

What do I do now?

Thanks!

---

### Post by Moonwings on 2008-01-27
bumping in the hopes someone will notice the post who can give a hand.
thanks

---

### Post by eombah on 2008-01-28
I had the same problem.
In my case, it was caused by the ~/.ssh directory and its contents being owned by root.
sudo chown -R myuser:myuser ~/.ssh solved it.

---

### Post by Moonwings on 2008-01-28
That was it!!!!!!!!!!!
Thank you so very much.
Problem solved :)

---

### Post by puelly on 2008-01-28
Thanks alot guys.  Helped me out also.

---

### Post by jolly79 on 2008-01-30
thanx dude... been banging my head over this.

---

### Post by danielhs on 2008-01-30
Fantastic.

I have a simple question: does this mean that I could SSH into my machine with just that key and without my password?

I'm a little confused since it's in my ~/.SSH.  Or does authorized_keys2 only refer to NX keys?


Daniel

---

### Post by hamlin on 2008-02-05
TNX for this solution. I had an[COLOR="Red"] NX> 505 ERROR: Error occurred: public key authentication failed.[/COLOR]
Changing the ownerschip of the .ssh from root to loginname worked fine:)

---

### Post by StatusWoe on 2008-02-13
Thanks a ton, These forums have answered every question I've had in 9 mths w/o me ever needing to ask one. 

You guys are great.

---

