---
title: "File sharing between two Dell Ubuntu 10.04 machines"
date: 2010-09-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jwaclawsky on 2010-09-04
I have two Dell machines running Ubuntu 10.04. Can anyone point me to information that I need to allow the machines to see each others files and work with them open, move, copy, etc. Thanks?

---

### Post by Dennis N on 2010-09-04
You can access files on the remote computer using Nautilus if the remote Ubuntu machine has the openssh-server package installed. So you need to install that first on the remote computer(s) that you wish to connect to. 

Basically, you can then connect to the remote computer from the local computer via the Places menu. The first time you connect, use "connect to server" and choose SSH for type of connection and fill in the IP address of the remote computer in the server box. I think there is also a box to bookmark the location. If you check that (and optionally provide a name), the remote computer shows up in the places menu (also in Nautilus bookmarks), and you should only need to click its entry and give the password (for the remote machine) to connect. 

(Note: The first time you try to connect you will get a warning. Ignore it and connect anyway.)

Community Documentation:

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

There are also lots of how-tos on SSH on the web dealing with more advanced topics.

---

### Post by jwaclawsky on 2010-09-07
Thanks Dennis N. I assume that is the best and easiest way to work with files such as documents, and charts from one machine and then store them back, with changes, on either machine. I am connecting the machines via my 802.11 network (so no Internet usage at this time, maybe later). Thanks!

---

### Post by ugm6hr on 2010-09-08
I agree, SSH is probably the simplest solution for you.

The other options, if you want to research them, are SMB (basically the Windows file sharing protocol), which seems a bit pointless unless there is a Windows system in the network, and NFS (a better protocol for Linux and others), which very good, does not have point and click activation, even in Ubuntu.

---

### Post by jwaclawsky on 2010-09-10
No windows ...I suspect gone forever from my household    :-)   

Thanks for the advice. I appreciate you sharing your wisdom!

---

### Post by SiathLinux on 2011-08-28
Nice information... 
But I do have a couple of questions (erm clarification)...

1. - I have Wired and WiFi - 3 versions of Windows + Ubuntu 8.04 (machine is old) + Ubuntu 6.10 (laptop is REALLY old) and want to have them all be able to access one of the 3 USB drives of my Ubuntu 8.04 machine - do I have to create a 'single' folder for the drive or is there a way just to have the drive be shared?

2. Does it have to have a 'log/pass' in order for my family to connect to that drive? (fyi - both Linux are mine - the rest of the family are running Windows XP/Vista/7)?

Thanks :)

---

### Post by mikewhatever on 2011-08-29
As mentioned above, Samba (SMB) is the solution for you. Search for a samba howto for 8.04.
For example: [http://www.jonathanmoeller.com/screed/?p=181](http://www.jonathanmoeller.com/screed/?p=181)

PS: I don't know how much success you might have with such a large mixture of different OSs.

---

