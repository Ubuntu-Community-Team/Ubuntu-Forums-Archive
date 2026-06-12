---
title: "Mount SMB Share with user's login"
date: 2009-02-25
forum: General Help
---

### Post by johnson8707 on 2009-02-25
Alright, so here is the environment:

I am trying to incorporate Ubunutu/Xubuntu machines into a windows network. I have gotten the machines to join the domain using Likewise open. I would like for the user's home folder (on an SMB Share) to be mapped and for the share to be mounted with the users login credentials (so the user can't access others files) I need this process to be automated because the people logging on to these machines will never have used Linux before. So I am trying to mirror what they are use to finding in Windows.


Here is what I am guessing??:
I've tried to configure Samba with no luck. I have desperately searched the web and found PAM_Mount to be the only thing close to what I need for this. But have not found any guides on how to use it.


If anyone can help me out with this I would be VERY grateful!

THANKS A LOT!!! :D

---

### Post by mckenna1977 on 2009-02-26
I hope this might help you some - I don't know how far you've gotten but I just set up similar using likewise-open so this post might help you...

[http://www.infoss.co.uk/2009/02/creating-a-network-file-server-using-samba-in-a-windows-environment/](http://www.infoss.co.uk/2009/02/creating-a-network-file-server-using-samba-in-a-windows-environment/)

Users from the domain can login and they're automatically created a home folder. Can't help with the network mapping or with pam mount but hopefully the above will help with auto-creation of the home folders and access from the network using domain\username with without having to enter credentials again.

peace...

---

