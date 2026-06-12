---
title: "Home Networking question..."
date: 2009-04-26
forum: General Help
---

### Post by Steven45 on 2009-04-26
Hi everyone

My room mate and myself have two computers in two different parts of the house. One has Ubuntu v9.04 (64-bit) installed on it and the other has Ubuntu v9.04 (32-bit) installed on it.

What we'd like to do is use the 32-bit computer to access files on the 64-bit computer. For example, let's say we had 10 YouTube videos stored in a folder on the 64-bit computer. We would like to be able to access (and watch them) on the 32-bit computer.

We have tried VNC but it is not working for this purpose and we don't really want to set up some huge Samba server type thing and start playing with the router, etc.

We were able to do this easily on Windows XP. Is there an equally easy method for doing this on Ubuntu 9.04?.

Thanks so Much...Steve

---

### Post by kanikilu on 2009-04-26
Yeah, VNC is not the appropriate solution to what you want to do...

I would normally recommend Samba or the **nautilus-share** package, but since they are both Ubuntu machines, why not use something like **sshfs** which will allow you to mount a remote directory via ssh.

[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

---

### Post by Cheesemill on 2009-04-26
You just need to set up NFS on the machines, there's a how to here:

[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html]("http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html")

Cheesemill

---

### Post by Steven45 on 2009-04-26
Thanks for fast replies and all the helpful info! :) .

I have decided to go with "nautilus-share" simply because it seems like the most user-friendly solution to me. I will be using this to access a folder on one computer and display the contents of that folder on another computer (videos, for example). Both computers have Ubuntu v9.04 installed.

I have gotten as far as selecting a folder on the 64-bit Ubuntu v9.04 computer and enabling it to be shared (read/write) but I am now very confused as to how I access this folder on the other Ubuntu computer (the 32-bit one).

Any help on this would be appreciated.

- Thanks again, Steve

---

