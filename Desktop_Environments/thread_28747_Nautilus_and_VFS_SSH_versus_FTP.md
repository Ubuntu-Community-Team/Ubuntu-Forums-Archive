---
title: "Nautilus and VFS: SSH versus FTP"
date: 2005-04-21
forum: Desktop Environments
---

### Post by Calvin on 2005-04-21
Hello everyone,

I'm having a little performance issue using Nautilus and VFS, meaning using the "Connect to Server..." option in Places.
Everything works perfectly when it comes to establishing the connection, and it's very simple, thanks to Gnome.

But when it comes to transferring big files with Nautilus, I'm having some performance trouble: sometimes the SSH connection is *very slow* (I need around 10-15 minutes to transfer a 700MB file from my computer to another computer) and if I use the FTP connection it only takes 1 to 2 minutes.

That makes me sure that it's not a problem of networking, because the speed is ok with ftp:// transfer via Nautilus, but not with ssh:// transfer. And what's very disturbing is that using "scp" in the command line, the speed is ok...

Am I the only one having this issue?  :roll:  :roll:

---

### Post by goebbe on 2005-04-22
The large differences in the transfer speed might be due to different
option:
SSH can transfer data
 - encrypted / not encrypted
 - compressed/ not compressed

I recomment to try different combinations to find out which one 
fits best to your needs.
So take a look at the documentation - and find out how you can
change the options for the ssh client.

---

