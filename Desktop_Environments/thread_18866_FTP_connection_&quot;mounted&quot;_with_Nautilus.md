---
title: "FTP connection &quot;mounted&quot; with Nautilus"
date: 2005-03-09
forum: Desktop Environments
---

### Post by kanten on 2005-03-09
Hi all,

I am trying to access a file on a remote ftp server, so that I can edit it directly on the server using Bluefish (a html/php editor). 

I think am supposed to be able to do that by using Gnome VFS, so using Nautilus I choose "Connect to server", etc. and a shortcut to my FTP server is created on the desktop. 
When I try to access the file in Bluefish, I can load the file just fine, but when trying to save it, Bluefish hangs.
When I look at the permissions for the connection I see that root is owner and that I don't have write permissions. I wasn't logged in as root, when I created the connection, so I don't get why root is owner, and I don't know how to create a connection with the proper permissions.

Anyone knows how to do this?

/Anders, Denmark

---

### Post by kanten on 2005-03-10
Bump

---

### Post by Julius on 2005-04-03
I'd like more info on this subject. I'm trying to do a "connect to server" thing, but my ftp username contains an @ symbol and it won't login properly :(

I'm compiling gnome-vfs-mount to see if I can make any achievement

---

### Post by kassetra on 2005-04-03
[QUOTE=kanten]When I look at the permissions for the connection I see that root is owner and that I don't have write permissions. I wasn't logged in as root, when I created the connection, so I don't get why root is owner, and I don't know how to create a connection with the proper permissions.
[/QUOTE]

Does the file on the other end have permissions for you to write to it?  A lot of times I get this when the file on the remote side doesn't have the correct permissions for me to write to it.

---

