---
title: "File sharing"
date: 2005-04-23
forum: Desktop Environments
---

### Post by fipeso on 2005-04-23
What is the easiest way in a home network to share files from a Ubuntu server to  Ubuntu client's ?

Is there a standard linux way of doing this?

How about printers?

---

### Post by heimo on 2005-04-23
[QUOTE=fipeso]What is the easiest way in a home network to share files from a Ubuntu server to  Ubuntu client's ?
[/QUOTE]
nfs or samba

[QUOTE=fipeso]
Is there a standard linux way of doing this?
[/QUOTE]
I don't think so. Use the most suitable. For instance - you could use Apache2 to share files. Or any one of those numerous ftp servers.

[QUOTE=fipeso]
How about printers?
[/QUOTE]
cups

:) Sorry for short answer. There's lots of information available on these subjects, when you know what to look for. Those should give you a good start. :)

---

### Post by Dr Gonzo on 2005-04-23
Use NFS.```
apt-get install nfs-kernel-server nfs-common
```Just do that on all the machines.

Now, on the server, you'll have a file called '/etc/exports' that contains all of the directories for the server to share.  In my file, I have an entry like this:```
/btorrent       192.168.1.101(rw,sync) 192.168.1.100(rw,sync)
```This means that the 2 IP addresses listed can mount the folder /btorrent on the server over NFS.

Now, on the client machines, you just mount the exported filesystems just like you would any other drive.  So, on the first machine listed above, we'd add this to /etc/fstab:```
192.168.1.102:/btorrent   /btorrent   nfs   defaults   0   0
```This assumes the server's IP address is 192.168.1.102, obviously.  This should now work. :) ```
mount -a
``` on the client.

NFS stands for Network FileSystem.  ```
man exports
```will give you more info on options for /etc/exports.

Note that you can make any of the machines export any directories to any computer on the network.  So, each machine can be both a client and a server.  For instance, I have a web server and I mount my ~/public_html directory on all of my machines so that I can just copy to it directly.  So, my main machine exports a couple of directories but also mounts some remote ones.

---

### Post by fipeso on 2005-04-23
Thank you,

This does clear things up a bit for a newbie Linux user :)

As samba is for connecting Linux to m$ shares, I rather take a look at nfs first :)

My kids do use win98 for their games, so maybe I have to samba or FTP later. 

With the detailed instructions from Dr Gonzo, I think I can get it to work, thank you .

Is nfs the "same" file system as Novell uses btw?

---

### Post by Dr Gonzo on 2005-04-23
I wouldn't be surprised, as I think NetWare is somehow related to BSD Unix.

BTW, once you install all of the NFS stuff, you can set up exports using the System->Administration->Shared Folders utility.  Just remembered that.  (I still use the CL method.  Old habits die hard.)

---

### Post by markp1989 on 2007-09-27
> **Dr Gonzo said:**
> Use NFS.```
apt-get install nfs-kernel-server nfs-common
```Just do that on all the machines.

Now, on the server, you'll have a file called '/etc/exports' that contains all of the directories for the server to share.  In my file, I have an entry like this:```
/btorrent       192.168.1.101(rw,sync) 192.168.1.100(rw,sync)
```This means that the 2 IP addresses listed can mount the folder /btorrent on the server over NFS.

Now, on the client machines, you just mount the exported filesystems just like you would any other drive.  So, on the first machine listed above, we'd add this to /etc/fstab:```
192.168.1.102:/btorrent   /btorrent   nfs   defaults   0   0
```This assumes the server's IP address is 192.168.1.102, obviously.  This should now work. :) ```
mount -a
``` on the client.

NFS stands for Network FileSystem.  ```
man exports
```will give you more info on options for /etc/exports.

Note that you can make any of the machines export any directories to any computer on the network.  So, each machine can be both a client and a server.  For instance, I have a web server and I mount my ~/public_html directory on all of my machines so that I can just copy to it directly.  So, my main machine exports a couple of directories but also mounts some remote ones.
 can you help me please, i do this then i get a warning saying 
mount: 10.0.0.1:/home/mark/Desktop/mymusic failed, reason given by server: Permission denied
and i don't know how i get permission, i right clicked on the folder i wanted to share, and selected "share folder"

---

