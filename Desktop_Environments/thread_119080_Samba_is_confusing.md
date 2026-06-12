---
title: "Samba is confusing"
date: 2006-01-18
forum: Desktop Environments
---

### Post by robtotheb on 2006-01-18
Newbie question....  I have a pc and laptop both running Ubuntu and want to share files between the two.  I presume I use Samba which ive installed... what now?  I dont need or want passwords or secruity, im not scared of my neighbours!

---

### Post by Biased turkey on 2006-01-18
Maybe using samba with just 2 Ubuntu systems is overkill. I would suggest using SSH instead.

---

### Post by audax321 on 2006-01-18
I suggest SSH as well: sudo apt-get install openssh-server

Since you have a laptop it will let you access your files from anywhere since it functions like a secure FTP. Also, as a side benefit you can run terminal commands on a remote computer by doing:

ssh user@address_to_server

Good luck.

---

### Post by robtotheb on 2006-01-18
great - thanks... trying now :)

---

### Post by robtotheb on 2006-01-18
intstalled it.  now what?

---

### Post by audax321 on 2006-01-18
To connect to a computer go to: Places > Connect to Server

Service Type: SSH
Server: Local IP to server (check ifconfig on the server) or Public IP (see note below)
Port: 22
Folder: just leave it blank, unless you want to go to a specific folder
Username: the user you are logged in as on the server
Name for connection: something descriptive

This will put an icon on your desktop to the computer as well as in the Places menu. Use it to access the server.

NOTE: If you want to access the server over the internet and your ISP uses Dynamic IP addresses, then setup DynDNS ([http://ubuntuguide.org/#assignhostnametodynamicip](http://ubuntuguide.org/#assignhostnametodynamicip))

---

### Post by robtotheb on 2006-01-18
Dont understand ....

Server: IP to server (check ifconfig on the server)

---

### Post by carlosqueso on 2006-01-18
you can also use NFS if it's safely on the same network.  However, DO not allow other computers to use it, as it is quite insecure once you get connected.  The following Howto is for Warty, but still works in Breezy.

[https://wiki.ubuntu.com/NFSServerHowTo?highlight=%28NFS%29](https://wiki.ubuntu.com/NFSServerHowTo?highlight=%28NFS%29)  

I managed to set up my 160GB HD in my desktop as a drive for my laptop with that.  If you need help with that I can try.

---

### Post by audax321 on 2006-01-18
Well let's say you installed openssh-server on your laptop. Then you would open a console and type ifconfig on your laptop and there will be a listing there with 

inet addr: XXX.XXX.XXX.XXX

Those numbers are your IP address. And that is what you enter on your desktop computer so it knows to access your laptop at that address.

---

### Post by robtotheb on 2006-01-18
Cool. Working now.  Thanks for your help

---

