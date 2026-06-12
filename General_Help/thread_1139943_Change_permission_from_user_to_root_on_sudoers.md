---
title: "Change permission from user to root on sudoers"
date: 2009-04-27
forum: General Help
---

### Post by whaler1 on 2009-04-27
Thinking it would be the easiest way to shuffle some folders around I went and changed the permission on the /etc folder from root to user using;
 
sudo chown -R steve.steve etc
 
unfortunately the sudoers file was included in this permission change and now I can't go and change the permissions back to root. I get the message;
 
sudo: /etc/sudoers is owned by uid 1000, should be 0
 
Could anyone possibly describe explicitly how I can undo this permission change?

---

### Post by DGortze380 on 2009-04-27
> **whaler1 said:**
> Thinking it would be the easiest way to shuffle some folders around I went and changed the permission on the /etc folder from root to user using;
 
sudo chown -R steve.steve etc
 
unfortunately the sudoers file was included in this permission change and now I can't go and change the permissions back to root. I get the message;
 
sudo: /etc/sudoers is owned by uid 1000, should be 0
 
Could anyone possibly describe explicitly how I can undo this permission change?

Hard Lesson Number One - Triple Check Permission Changes First.

You can 'undo' it. You'll need to know the default owner and groups for all files and folders in /etc and change them back one by one (or in chunks if possible) from a root shell.

Good Luck. Most of the time it's easier to back up your files and reinstall.

---

