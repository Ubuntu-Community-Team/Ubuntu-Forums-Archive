---
title: "Samba share - user levels"
date: 2006-07-25
forum: Desktop Environments
---

### Post by Flavian on 2006-07-25
Hi folks
I got a question concerning samba.
I set up samba without a problem on my server, everything runs smothly (at the moment I am copying Data to the disc, so I can't tell a 100%, but I can see the shares and access it)

There is still a question remaining, maybe I didn't get it or read over it, hopefully someone can help me.
In Windows I had user level shares set up, that means you could access data on the which was set for your specific user to be viewed and / or modified, but others couldn't.
You proboably all know how it works in windows. You set a user permission for a folder and that's it.

How can I do that with Samba shares, do I have to write something in "create mask = ..." and if yes, what? and if so how can I deny access to the folder let's say for my brother?

Thanks in advance.
Florian

---

### Post by Thund3rstruck on 2006-07-27
Yes modify your /etc/samba/smb.conf file and define user permissions for the share. Refer to the man for detailed examples

```

$ man smb.conf

```

---

### Post by Flavian on 2006-07-31
Can someone maybe post such a samba config file, since I am very new in using Linux.
That would help me a lot!
Thanks in advance
Flo

---

