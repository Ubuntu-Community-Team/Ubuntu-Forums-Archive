---
title: "User accounts question"
date: 2009-02-24
forum: General Help
---

### Post by mike0020 on 2009-02-24
I have two computers in my house connected over a network. The one I'm using right now currently has Ubuntu on it and the other one is running Windows XP. I want to run Ubuntu on that computer as well, however I have a question that needs to be answered because doing so.

I want to be able to have four user accounts over the network (including my own), one for each member of my household. I want each person in my household to be able to access their accounts through either computer, but I'm not sure how I could put the user accounts over a network. If someone could please tell me how I could do this I would be very grateful.

---

### Post by Vaphell on 2009-02-24
if i understand correctly you want to have shared home folders, so users have exactly one set of personal data, not two?

if so - my general idea would be to share user home folders on server machine using samba and then to mount them to appropriate folders on client machine during startup, probably using entries in /etc/fstab. I am not sure if it would work though, i am not an expert.
I am curious how such thing can be done so i am waiting for precise instructions. Good luck :)

---

### Post by mike0020 on 2009-02-25
bump

---

### Post by Veyasu on 2009-02-25
I think he means having something similar to Active Directory for Windows.

Theres something called OpenLDAP which can do something similar I believe, but I've never tried it, and reading forums, I think it's quite alot more difficult than setting up a Windows domain. But I really don't know, I've never tried it.

---

### Post by mike0020 on 2009-02-26
So is there no straight answer to my question?

---

### Post by cariboo on 2009-02-26
I would probably use samba on one  of the computers and mount the shares in the /home directory on the other computer, of course this depends on both computers running in order for that to work.

Have a look at this [Samba howto]("http://ubuntuforums.org/showthread.php?t=202605")

and

[Mount]("http://ubuntuforums.org/showthread.php?t=288534") samba shares.

Jim

---

### Post by mb_webguy on 2009-02-26
Actually, the problem is that there are *numerous* straight answers to your question.  It just depends on how you want to go about doing it.

If you actually want users logging into the exact same account regardless of the physical machine they're using, then you're looking at a remote login with a server-client setup.  On the positive side, a user only has one account, period, no matter which machine they're physically using at the time.  On the downside, the server is going to be doing all of the work, so it needs to have a lot of system resources (i.e. the fastest processor, the most memory, good video and sound cards, etc.), and preferably all of the storage.  In this setup, the client machines have little need for hard drives or memory (and could theoretically even boot from a CD with no hard drive at all).  You could load up the server with hard drives and memory pulled from the clients.  Even if you don't remove the hard drives from the clients completely, you'd at the very least want to move the larger ones to the server.

On the other hand, if you don't want to be rearranging hardware, you could set up identical accounts on each computer and set up filesharing so a user can access his home folder on another computer.  You could even set up VNC so you could do a remote login from one to the other.  This is in one sense simpler, since you're dealing with each computer individually.  Also, one person using one computer won't affect the performance of another person using another computer -- which could certainly happen if they were both logged in to the same server.  On the other hand, unless you have some sort of script running to mirror a user's settings across the various computers, changes made to an account on one computer won't affect the corresponding account on another computer.  And this setup can be considerably more complicated from the user's perspective, since unless you get very creative in mounting your network shares, a user has to remember on which computer a given piece of data was stored.

And there are other solutions as well, with different degrees of difficulty of setup and convenience of use.  So I don't think it's that people can't give you a straight answer, it's rather that they don't know which answer to give.

---

