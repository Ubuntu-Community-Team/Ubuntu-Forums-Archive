---
title: "share files breezy to breezy"
date: 2005-12-18
forum: General Help
---

### Post by Benchrest on 2005-12-18
I've found alot on sharing windows to breezy files with samba and I have that working. I have two systems that are both dual boot. I can run windows on either machine and breezy on the other and share files. But if both are booted to breezy I cann't figure it out. Looks like NFS might be the answer except I don't think I can have both Samba and NFS. Is this correct? Please point me in the right direction.

---

### Post by BathroomNinja on 2005-12-18
I'm currently using NFS on a laptop, and samba at the same time.  I use them for 2 dirrerent purposes.

I use NFS to automount a /home/user/documents folder at boot on the laptop.  I share a media folder using samba since it doesnt have to load up at boot.  Hence, when I take the laptop out of my home, I don't have any issues.

What exaclty are you trying to share, and how do you have it setup at the moment?  Are you trying to mount a folder at boot, or what?

---

### Post by zoiks on 2005-12-19
[QUOTE=Benchrest]I've found alot on sharing windows to breezy files with samba and I have that working. I have two systems that are both dual boot. I can run windows on either machine and breezy on the other and share files. But if both are booted to breezy I cann't figure it out. Looks like NFS might be the answer except I don't think I can have both Samba and NFS. Is this correct? Please point me in the right direction.[/QUOTE]

You can certainly use nfs and samba at the same time.  You might be better off sticking to samba since that means you only have to maintain one sharing system.  AFAIK, there are two ways to access a share from ubuntu.  One is you can mount the share to a mount point in your ubuntu system using smbfs.  The other is you can access a samba share on-the-fly by opening a nautilus file manager window, hitting <ctrl>-L, and entering 

```
smb://hostname/sharename
```

in the address box.

---

### Post by gosh on 2005-12-19
I have a similar problem.

I installed Ubuntu on my desktop and my notebook.
I have installed XP on another desktop and another notebook.

What works?
- share printers and files on Ubuntu desktop from XP-machines

Wat doesn't work?
- share printers and files from Ubuntu notebook to Ubuntu Desktop and vice versa. When I try to browse the shared folders it asks for a password.

This is my smb.conf:
[global]
	workgroup = WORKGROUP
	security = share
	printable = no
	read only = no
	encrypt passwords = no
	print command = lpr -P %p -o raw %s -r
	load printers = yes
	printing = cups

wins support = no
[homes]
	browseable = yes
	writeable = yes

[printers]
	comment = All Printers
	browseable = yes
	path = /tmp
	printable = yes
	create mask = 0700

[jos]
path = /home/jos
comment = jos on ubuntu
available = yes
browseable = yes
public = yes
writable = yes

[USBDisk]
path = /media/USB DISK

available = yes
browseable = yes
public = yes
writable = yes

---

### Post by Benchrest on 2005-12-19
I'm trying to share files for converting from windows to Ubuntu. For instance after getting Samba working with the Laptop (Ubuntu) Desktop (windows) I then reversed it. I took the SMB.CONF file from the Laptop and put it on the desktop. I have a common windows folder I used that Ubuntu can access from either machine. I forsee more of this as I migrate. I have all four operating systems with the same user id and password to make it simpler. Also with windows I use the desktop to backup the laptop. I want to continue that after I convert.

I thought Samba was only for a Linux machine to share files with a windows machine? Not Linux to Linux. I will  try some of your suggestions this evening. Thanks for the replies.

---

### Post by maglis on 2005-12-19
I want to suggest another angle of approach which I think is simpler to setup:

Use of SSH on all operating systems.

You will need a service and a client for each operating system:[LIST]
[*]Linux side:[LIST]
[*]SSH server package "openssh-server"
[*]SSH client package "openssh-client". You can browse any SSH server via nautilus (ssh://<USER>@<SSH-SERVER>) or by creating a permanent ssh type connection to server from "Places -> Connect to server..." menu.[/LIST] 
[*]Windows side:[LIST]
[*]SSH server: Have a look in these places:[LIST]
[*][http://pigtail.net/LRP/printsrv/cygwin-sshd.html]("http://pigtail.net/LRP/printsrv/cygwin-sshd.html")
[*][http://sshwindows.sourceforge.net/]("http://sshwindows.sourceforge.net/")[/LIST] 
[*]SSH client: can have a look at [http://www.openssh.com/windows.html]("http://www.openssh.com/windows.html") , but I would suggest either [WinSCP]("http://winscp.net/") or [FileZilla]("http://filezilla.sourceforge.net/") .[/LIST] [/LIST]

---

