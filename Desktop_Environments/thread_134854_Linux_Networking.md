---
title: "Linux Networking"
date: 2006-02-22
forum: Desktop Environments
---

### Post by jcstoronto on 2006-02-22
Hi Ubuntu World...

I have several computers that make up my home network. I have no problem connecting (printer/file sharing) anyone of my 5 Linux (Ubuntu) computers to my 2 Windows laptop computers, but the problem is when I try to connect a Linux computer to another Linux computer. I have tried using the "Connect to Server..." feature by creating an FTP connection with each computer, even trying the Smb4k program to noavail!:confused: 
Can anyone suggest an easy way to connect 2 Ubuntu computers together for the purpose of file sharing?

Thanks, JCS.

---

### Post by deBaas on 2006-02-22
Using samba?

---

### Post by jcstoronto on 2006-02-22
yep... even Samba.
Like I said, I have no problem connecting to a Windows shared computer, even a remote Windows shared computer via a VPN connection.

JCS

---

### Post by jchau on 2006-02-22
This may be a little excessive (in terms of security) for a private home network, but you can set up a openssh server & allow sftp (or sftp or scp only through rssh).  

If you want to limit the access for the sftp user, you can follow this:
[http://www.ubuntuforums.org/showthread.php?t=128206](http://www.ubuntuforums.org/showthread.php?t=128206)

This way, you can securely share files over the internet (encrypted connection & user and passwd needed to connect).  

That is what I did to share files. :-D

---

### Post by stevea1210 on 2006-02-22
Let's back up a step.  
Can you  ping the linux pc's via unc name from another linux pc?  
How about ping a windows pc from linux via unc name
Thirdly, ping windows from linux via unc name.

Just want to make sure the whole problem isn't dns.

---

### Post by jchau on 2006-02-22
> Just want to make sure the whole problem isn't dns.

You probably need a dhcp server in there somewhere.  If you have a router in there, the router should most likely do the job.

---

### Post by Tichondrius on 2006-02-22
[QUOTE=jcstoronto]Hi Ubuntu World...

I have several computers that make up my home network. I have no problem connecting (printer/file sharing) anyone of my 5 Linux (Ubuntu) computers to my 2 Windows laptop computers, but the problem is when I try to connect a Linux computer to another Linux computer. I have tried using the "Connect to Server..." feature by creating an FTP connection with each computer, even trying the Smb4k program to noavail!:confused: 
Can anyone suggest an easy way to connect 2 Ubuntu computers together for the purpose of file sharing?

Thanks, JCS.[/QUOTE]

I assume you can ping each computer from any other computer on your network.

Now, before you can connect using FTP, SSH, NFS, SMB or HTTP you first need to set up the appropriate server on the destination computer.  I suggest that first you install SSH server on all your Linux machines (because it's the most general purpose) as described here:

[http://easylinux.info/wiki/Ubuntu#SSH_Server](http://easylinux.info/wiki/Ubuntu#SSH_Server)

Once you have that, you can connect to that machine from another Ububtu machine using connect to server menu item (and choose SSH as the servie type). To connect to the SSH server from a windows machine you need to use a SSH client like WinSCP which is a free download. 

The other ways to share files are using SMB or NFS, which are both remote filesystem protocols, but NFS is much better if all you need is to share files between linux machines. Here's how to do that:

HowTO setup NFS server: [https://wiki.ubuntu.com/NFSServerHowTo?highlight=%28nfs%29](https://wiki.ubuntu.com/NFSServerHowTo?highlight=%28nfs%29)
HowTo setup NFS client: [https://wiki.ubuntu.com/NFSClientHowTo?highlight=%28nfs%29](https://wiki.ubuntu.com/NFSClientHowTo?highlight=%28nfs%29)

I set up all my Linux machines as NFS servers, as well as NFS clients with the auto-mounter, so I can access any machine's files from any other machine using the path /net/machine-name.

You can also set up a samba server on your linux machine, so windows machines can browse the files from the network neighborhood (this is a little nicer than having to use a SSH client like WinSCP because you can just browse the files in Windows Explorer):

[http://easylinux.info/wiki/Ubuntu#Samba_Server](http://easylinux.info/wiki/Ubuntu#Samba_Server)

Finally you can use HTTP to share files. That's right, if you have a web server running on a machine, other machines can use a web browser to see the files it's exporting (by default it's only the /var/www directory), and download them. Here's how to install apache web server:

[http://easylinux.info/wiki/Ubuntu#Apache_HTTP_Server](http://easylinux.info/wiki/Ubuntu#Apache_HTTP_Server)

Note about firewalls: If you are running a software firewall (e.g. firestarter) on any of the Ubuntu machine's, make sure you set it to allow incoming connections originating from your local network for the ports used by SSH, NFS, SMB and HTTP. Firestarter will alert you (by flashing a red lightning) about this if you don't open the ports first, and it's easy to instruct it to allow these connections.

I've got all the above methods working flawlessly. Not to mention remote desktop, VNC, and NX, which are remote desktop protocols and serve a different purpose than remote file transfer protocols like the ones described above.

---

### Post by jcstoronto on 2006-02-23
Thanks Tichondrius.... I will try the Samba Server aprroach using the NFS options tomorrow... I will let you know how it turned out.

JCS

---

### Post by Tichondrius on 2006-02-23
[QUOTE=jcstoronto]Thanks Tichondrius.... I will try the Samba Server aprroach using the NFS options tomorrow... I will let you know how it turned out.

JCS[/QUOTE]

Great, but you should also set up the SSH server - it's the simplest and most useful secure communication protocol as it allows remote logins, secure file-copying (SCP), and secure FTP (SFTP). SSH replaces all the old unsecure protocols like telnet, rlogin, ftp, rcp, etc.
  SSH client is included in the base Ubuntu distro (as well as most other linux distro), and like I mentioned there are SSH clients for windows, the best being WinSCP for file transfer (support SCP and SFTP), and putty for remote logins. Both are free downloads for windows.
  SMB is different than SFTP/SCP, since it's a remote file system protocol. First you need to configure the server and designate which directories to export (and user permissions), and then the client Linux machine needs to mount those filesystem as described in the guide. From windows, you just need to add a network place for the Samba server machine, so you'll be able to browse it just like any other remote shared folder.

It's perfectly OK to set up more than one of these servers and protocols, since each one has its own advantages and they don't interfere with each other. I think SSH is a basic service, but Ubuntu chose not to include it in the base distro because some people don't want to allow any incoming connections. But for home usrs which have their machines behind a NAT firewall router (like most users have) there is no concern about incoming connections from the internet since the router will block all of them.

---

### Post by jcstoronto on 2006-02-23
Thanks for all the info Tichondrius...

I decided to go with the NFS Server & Client route.... this worked like a charm. Now all my computers (Linux & Windows) are sharing beautifully.

JCS

---

