---
title: "Ubuntu, Active Directory and roaming homedirs"
date: 2009-11-22
forum: Desktop Environments
---

### Post by safi78 on 2009-11-22
Hi all,

I've googled around and searched the forums but I really can't find a decent solution to this:

I wanna completely move away from our Windows desktops and use Ubuntu.

We implemented likewise-open to authenticate against our Active Directory very successfully. likewise creates homedirs like /home/DOMAIN/username

Is there an easy way to 'remote-mount' the /home/DOMAIN/username to a server so the home dirs are stored there so my users can roam around and have their settings available on every desktop?

I'm familiar NFS or Samba but I read there's alot of messy permissions-configuration with that. Anyone with any experience on this?

Furthermore, are there any good administration tools for administring a lot of desktops? (like installing and removing packages on all the desktops at once, pushing settings to all the desktops etc.) ?

---

### Post by Bufke on 2010-02-09
I would like to know how to do this too.

---

### Post by bonevg on 2010-02-09
> **safi78 said:**
> 
Furthermore, are there any good administration tools for administring a lot of desktops? (like installing and removing packages on all the desktops at once, pushing settings to all the desktops etc.) ?

For that part of your question you may find useful tool called cfengine.

---

### Post by lykwydchykyn on 2010-02-09
> **safi78 said:**
> Hi all,

I've googled around and searched the forums but I really can't find a decent solution to this:

I wanna completely move away from our Windows desktops and use Ubuntu.

We implemented likewise-open to authenticate against our Active Directory very successfully. likewise creates homedirs like /home/DOMAIN/username

Is there an easy way to 'remote-mount' the /home/DOMAIN/username to a server so the home dirs are stored there so my users can roam around and have their settings available on every desktop?

I'm familiar NFS or Samba but I read there's alot of messy permissions-configuration with that. Anyone with any experience on this?

What's your server running?  If it's running Windows, samba is probably the best bet.  The "samba 3 by example" guide is a great resource here.
[http://www.samba.org/samba/docs/man/Samba-Guide/](http://www.samba.org/samba/docs/man/Samba-Guide/)

I'm afraid I haven't used likewise much, though, so I can't comment on that one. 
> 
Furthermore, are there any good administration tools for administring a lot of desktops? (like installing and removing packages on all the desktops at once, pushing settings to all the desktops etc.) ?

cfengine was mentioned, though frankly I could never get my head around it.  Other choices are:
 - Puppet
 - Webmin has a "cluster" feature that works ok for small numbers of machines
 - Canonical has a (commercial) tool called "landscape" designed for just this.  It's not free though.

How many machines are we talking about?

---

