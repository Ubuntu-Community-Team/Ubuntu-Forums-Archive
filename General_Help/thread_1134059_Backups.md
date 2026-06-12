---
title: "Backups"
date: 2009-04-23
forum: General Help
---

### Post by Wastedyouthfx0 on 2009-04-23
I have a Windows PDC with about 25 networked computers.  I've added an Ubuntu server to the mix, which I'm absolutely loving and ist been taking over duties of the network one by one.

My question, any way to make my Ubuntu backup 25 windows workstations?  Can anyone point me in a good direction?

---

### Post by kanikilu on 2009-04-23
I've heard good things about Bacula, but haven't had a chance to try it out for myself yet.

[http://www.bacula.org/en/](http://www.bacula.org/en/)

Also, if that's overkill for your needs, another solution would be to just use the Ubuntu box as an SMB file server and have the clients do their own backups to a shared folder on the server.

That way they can have control over what gets backed up, when it gets backed up, and what software to use. On Windows, I've had pretty good results with Cobian - a free, full-featured backup software...

---

### Post by Wastedyouthfx0 on 2009-04-24
> **kanikilu said:**
> I've heard good things about Bacula, but haven't had a chance to try it out for myself yet.

[http://www.bacula.org/en/](http://www.bacula.org/en/)

Also, if that's overkill for your needs, another solution would be to just use the Ubuntu box as an SMB file server and have the clients do their own backups to a shared folder on the server.

That way they can have control over what gets backed up, when it gets backed up, and what software to use. On Windows, I've had pretty good results with Cobian - a free, full-featured backup software...

I'm one of those people who like overkill.  I don't know enough about Bacula so I'll have to research it more, but just looking over it I really like what I'm seeing.  Thanks for the recommendation.  I saw some other solutions involving rsync, but I'm going to try this one out and share the results I suppose.

I really love Ubuntu.  The solution to all my complicated questions is always sudo apt-get install.

---

### Post by kanikilu on 2009-04-24
> **Wastedyouthfx0 said:**
> Thanks for the recommendation.  I saw some other solutions involving rsync, but I'm going to try this one out and share the results I suppose. Cool, let us know if it works for you. I've been meaning to try it but always get sidetracked (most recently with setting up Nagios for network monitoring ;) )

> I really love Ubuntu.  **The solution to all my complicated questions is always sudo apt-get install**. Hehe, I might have to make that my sig :D

---

