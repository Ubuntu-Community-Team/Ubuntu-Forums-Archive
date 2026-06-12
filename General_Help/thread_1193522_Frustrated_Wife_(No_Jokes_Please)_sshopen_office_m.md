---
title: "Frustrated Wife (No Jokes Please) ssh/open office might be permissions?????"
date: 2009-06-21
forum: General Help
---

### Post by nothingspecial on 2009-06-21
I get my wife to back her college work up to the headless server under the stairs.

She cannot/will not use the terminal.

She has a bookmark in nautilus to access the server.

She navigates server > media > backup > suzie > college

When she clicks on a file to open with open office a window opens asking her to " Enter the username and password for 192.168.2.8 here"

There is no box to enter the username (which is mine). She enters the correct password and nothing happens.

When she closes the dialogue window open office reports a "general internet error"

From my laptop I just click on any file in her folder and it opens.

I have tried chmod -R 777ing her folder but nothing gives.

Anyone help?

Thanks!

---

### Post by cmost on 2009-06-21
Hello!  I've been running a Linux server in my home that Masquerades as a Windows server for years!  I do a lot of IT work on the side and I've had occasion to connect many an outside computer to my server for backups etc.  Over the years I've discovered what tricks to use to ensure things run smoothly regardless of what type of clients I connect (e.g., Windows, Macintosh or Linux).  How do you have your server setup?  Are you running a SAMBA server or an NFS server?  Which distribution have you on your Server?  Please give me a little info and I'll see if I can assist you.

---

### Post by nothingspecial on 2009-06-21
Thanks for your reply.

This is a "server" in the loosest term of the word. The only outside access is through ssh to access my music. I run mt-daapd and squeezecenter.

Really it is just a media file and backup server for our home network. Everything is accessed through ssh.

I can open my wife`s files from her laptop typing ooffice -writer /path/to/file but cannot manage it the gui way.

I`m talking about (in gnome) places > connect to server > ssh > user@ip > file.

It will not let her connect - this has to be point and click

---

### Post by JordyD on 2009-06-21
Instead of user@ip in the "Connect to server..." dialog, type the ip in the "Server" field, then the username in the "User Name" field.

EDIT: Err, nevermind, it makes no difference.

---

### Post by blueridgedog on 2009-06-21
I would setup keys versus username and passwords for the ssh connection.

[http://www.sshkeychain.org/mirrors/SSH-with-Keys-HOWTO/](http://www.sshkeychain.org/mirrors/SSH-with-Keys-HOWTO/)

If you generate a key without a passphrase under her user account, then place that key in the config file on the server, she should be able to connect seamlessly.

---

### Post by cmost on 2009-06-22
I don't know.  Using SSH and generating keys, etc. seems like overkill and unnecessarily difficult.  I would simply setup your server as a simple SAMBA server.  Once you have it configured, you'll easily be able to map shares using fstab in Linux/UNIX systems or map a network drive permanently on Windows boxes.  Here's how I would go about it:

1.  Install the SAMBA packages on the server
2.  As root, edit /etc/samba/smb.conf; paste in your own personal variation of the following (i.e., customize for the shares you want - be sure the hosts allowed matches your local network IP range; make sure you select a username that exists on the server; make sure the path to the shared folder exists on the server!

#========== Global Parameters ==========#
[global]
workgroup = WORKGROUP
netbios name = YOUR SERVER'S NAME
server string = Ubuntu Linux file Server
security = user
encrypt passwords = true
hosts allow = 192.168.10.0/255.255.255.0 localhost
hosts deny = All
printcap name = cups
show add printer wizard = No
printing = cups
local master = yes
preferred master = yes
os level = 65
lm announce = yes
lm interval = 60

# Messeging (through winpopup)
message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

#========== Global Share Parameters ==========#
create mask = 0744
directory mask = 0744
case sensitive = no
hide dot files = yes
read only = no
force user = username
force group = users

[printers]
comment = All Printers
path = /var/spool/samba
printer admin = root, cmost
create mask = 0600
guest ok = Yes
printable = Yes
use client driver = Yes
browseable = no

#========== Home Folders ==========#
[homes]
	comment = Personal home directory
	valid users = %S
	read only = No
	browseable = No


#========== Shared Folders ==========#

[SHARE]
	path = /path/to/server/SHARE/
	comment = Shared folder on this file server

3.  Add the samba user (e.g., this is the username and password you'll enter the first time you access the shared folder from another computer!)  Note:  you might want to make this the same user name listed in "force user = username" in the smb.conf

On the server, as root, type the following:

sudo smbpasswd –a username

4.  Restart the SAMBA server

sudo /etc/samba/samba restart

5.  You're done!

Now you have your own SAMBA server for easy access to your file server and shared files and folders.

---

### Post by nothingspecial on 2009-06-23
Thanks for your suggestions.

She can play music from the daap share, no problem. She can navigate the servers file system through nautilus aswell. She can copy her files to the server.

We can watch videos over the network (although I haven`t tried on her laptop). Everything is set up nicely and works. 

The only problem is she can`t open her open office files on her laptop from the server. I can open them in nautilus on any other box on the network and from the command line on her laptop.

I just struggling to understand why she can`t click on a file (residing on the server but mounted on her laptop) and open office will open it when the other 3 computers can. And they are her files.

---

