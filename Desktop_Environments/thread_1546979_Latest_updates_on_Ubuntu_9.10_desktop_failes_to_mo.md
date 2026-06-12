---
title: "Latest updates on Ubuntu 9.10 desktop failes to mount windows share on network drives"
date: 2010-08-06
forum: Desktop Environments
---

### Post by rjkothari on 2010-08-06
After latest updates on Ubuntu 9.10 desktop today - network connection to Samba share on a network drive have stopped working. 

I'm getting following error in Nautilus
-----------
Error: Failed to mount Windows share
Please select another viewer and try again.
------------
Any idea how to resolve this issue?

Rajesh Kothari

---

### Post by rjkothari on 2010-08-11
I'm not sure what happened. But I found 'samba' was not there. So installed samba using 'sudo apt-get install samba'. It gave few errors. Removed it. Reinstalled. Even 'smbfs' was not there. Installed it similarly. Still it did not work.

After trying out several shares (existing) one worked flawlessly. After some investigation I noticed that in this share - in the 'Server' field instead of usual <server name> I had put ip address of the server. So, deleted all existing shares and recreated them using server's ip address. It worked like charm. Not sure why this should happen. Any idea?

---

