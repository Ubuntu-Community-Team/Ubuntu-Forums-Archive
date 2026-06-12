---
title: "Local Networking"
date: 2009-05-02
forum: General Help
---

### Post by mxboy15u on 2009-05-02
I am having a lot of trouble doing this. Why is it so easy to network with a windows computer and so hard to do it with another ubuntu computer?

I want to link 2 ubuntu computers for file transfer. I have followed the SSH guide and not been able to get them to talk. Bonjour just allows 1 file at a time and that is unacceptable. Giver does not play well with Jaunty and the notification that a file is trying to get transferred never appears. 

There has to be a way to make the computer discoverable, log in and transfer files, can someone please help me?

---

### Post by cmnorton on 2009-05-02
Briefly, what is the configuration of your network?

---

### Post by mxboy15u on 2009-05-02
Nothing fancy, just 1 linksys router with factory settings, 3 ubuntu computers 1 vista computer and 1 xp computer. The ubuntu computers talk to the windows computers perfectly, but I have not gotten them to talk to each other yet.

---

### Post by cmnorton on 2009-05-02
Is your firewall running? It's usually on by default. You don't have to shut it off, but you'll have to provide an access list.

---

### Post by gsgleason on 2009-05-02
> **mxboy15u said:**
> Nothing fancy, just 1 linksys router with factory settings, 3 ubuntu computers 1 vista computer and 1 xp computer. The ubuntu computers talk to the windows computers perfectly, but I have not gotten them to talk to each other yet.

Talk to each other?  Please elaborate.

---

### Post by mxboy15u on 2009-05-03
I just want to network together, to see the shared folders and to transfer files between computers.

---

### Post by Iowan on 2009-05-03
> **mxboy15u said:**
>  I have followed the SSH guide and not been able to get them to talk.  [This]("https://help.ubuntu.com/community/SSHHowto") one?  There is also a help pages on [SSHFS]("https://help.ubuntu.com/community/SSHFS").

---

### Post by cmnorton on 2009-05-03
> **mxboy15u said:**
> I just want to network together, to see the shared folders and to transfer files between computers.

The suggestions here are to get you to go through stepwise refinement in debugging this process. For example, can you ping each node from the other? And, how are the firewalls on each Ubuntu system set up? That will tell you a lot, too.

---

