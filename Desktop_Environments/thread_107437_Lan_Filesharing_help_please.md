---
title: "Lan Filesharing help please"
date: 2005-12-23
forum: Desktop Environments
---

### Post by morganw25 on 2005-12-23
I installed LinNeighborhood successfully on both my Ubuntu computers.
I have one as a gateway to the net(cable  modem) and the other connected to the first via hub using dhcp.

Both computers can access the net without problems. I used firestarter to allow the second pc to connect to the internet.

I am currently having issues finding an easy way to share folders between the two computers. Like I said I installed LinNeighborhood by using Synaptic and it loaded some smb program as well.  I installed LinNeighborhood as the user and not root. 

Whenever I try and use LinNeighborhood to add a machine it doesn't see any other pc on the network other than the one LinNeighborhood is installed on.

Can someone please help me setup files that will be shared between the two computers on boot up.

---

### Post by zoiks on 2005-12-24
You can use either samba

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

or NFS.  If you are sharing only amongst Linux computers, NFS is the best.

[http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)

You may also investigate regular ole ftp or sftp, as well as some gnome filesharing thingy that I don't know anything about.

---

