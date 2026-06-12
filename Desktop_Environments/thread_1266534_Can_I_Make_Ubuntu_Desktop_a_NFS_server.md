---
title: "Can I Make Ubuntu Desktop a NFS server"
date: 2009-09-14
forum: Desktop Environments
---

### Post by larka06 on 2009-09-14
I am using jaunty for a desktop and I wish to share files with other computers also running jaunty.  I also wish to share my printer with the other computers.  I am thinking NFS at the moment, do know how to do it with samba.  Any advice is appreciated
Thanks all for time and effort

---

### Post by abaden on 2009-09-14
I found [this]("http://nfs.sourceforge.net/nfs-howto/") a few weeks ago in another thread.

I accomplished the same thing with my network using samba, and it wasn't [too] painful. I don't have too much experience with NFS though, so I can't comment on which is better.  

Just a note, you will need to create a new partition for NFS, whereas with Samba you can just share existing folders. This might be something to consider as you decide which option to choose.


Alex

---

### Post by larka06 on 2009-09-15
Thanks Alex The info is good and no I hadn't thought about having to use a new partion. I hadn't thought of it because I have never done NFS. Never doing it is the reason I was considering doing it.  I have done Samba and it is easy, although I have not tried to use Ubuntu desktop to do it with.  It seems that the desktop has no server software which is good in someways but, using it as a dual purpose causes me to question.  I will check out the link
Thanks agian

---

### Post by abaden on 2009-09-15
> **larka06 said:**
> It seems that the desktop has no server software which is good in someways but, using it as a dual purpose causes me to question. 

By default the desktop installation doesn't really come with any server software. That isn't to say you can't install any though - packages are global across both distributions (for example, you could put a gui on the server distribution if you really wanted to).

Best of luck!
Alex

---

