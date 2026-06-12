---
title: "connecting two ubuntu pc's through local wireless"
date: 2009-05-29
forum: General Help
---

### Post by jakupl on 2009-05-29
I Have three ubuntu ps's in my household, and I want to be able to pull files from computer to computer without running around with a usb stick. And preferrably without having to attend to the computer that I want to connect to. I have tried to use the inbuilt remote desktop thing but it just does not work. What am I doing wrong? I am suspecting that it has something to do with port forwarding in my wireless router, but I have no idea how to fix it.
Any help is much appreciated.

---

### Post by pennacook on 2009-05-29
You really shouldn't need port forwarding to do this if they are all local. 
So, have you enabled viewing and sharing of your desktop? Then from the other ubuntu system, use vinagre to connect to it?

---

### Post by jakupl on 2009-05-29
> **pennacook said:**
> You really shouldn't need port forwarding to do this if they are all local. 
So, have you enabled viewing and sharing of your desktop? Then from the other ubuntu system, use vinagre to connect to it?

well, suddently it works, but really badly. It hangs all the time, and how do I move files from that computer to this computer?

---

### Post by ghindo on 2009-05-29
To access machines on my local network, I just use ssh.  If you install the "ssh" package on each of your three machines, you would be able to easily access each machine through ssh.

---

### Post by Matt Yun on 2009-05-29
scp (the file copy command from the OpenSSH package) is the easiest way to copy files from one computer to another over a wired or wireless network.  You will need to setup an ssh server on one or both of your computers.  Fortunately, in Ubuntu, it's really easy:  [Beginning SSH tutorial]("http://principialabs.com/beginning-ssh-on-ubuntu/").

---

### Post by ghindo on 2009-05-29
You can even make it one step easier than that.  If you're running normal, GNOME Ubuntu, then you already have a good graphical interface to ssh.  Just go to "Places" -> "Connect to Server..." and then connect to the desired computer (like you see in the attached picture).

---

### Post by paradigm2 on 2009-05-29
I would probably go with sshfs.

[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

It is far superior to Samba for Linux machines.  You will be able to securely mount the remote filesystem as if it were local.  It is even easier to install than Samba too (usually!).

---

### Post by tyroeternal on 2009-05-29
Here is the ubuntu help page for sharing documents on Ubuntu.  This sounds like it is what you are looking for, if not let us know!  [https://help.ubuntu.com/9.04/internet/C/networking-shares.html](https://help.ubuntu.com/9.04/internet/C/networking-shares.html)

---

### Post by jakupl on 2009-05-29
> **ghindo said:**
> To access machines on my local network, I just use ssh.  If you install the "ssh" package on each of your three machines, you would be able to easily access each machine through ssh.

wooow yeeeah it works beautifully. I can log in to the other machines, but is this altso possible when I am in a different country eg.? how would one connect to a remote host? and how on earth do I copy a file from that machine to this machine? would it be something like cp "filename" "this host" "filename"  ... no right?
I know, I should read the documentation

---

### Post by tyroeternal on 2009-05-29
To connect to a remote host (in another country even) you would essentially need their ip address or hostname, and have the connection able to get through (not behind a firewall that blocks it).

And reading the help and manual pages is an excellent way to learn much more than we can tell you :D

---

### Post by ghindo on 2009-05-29
> **jakupl said:**
> wooow yeeeah it works beautifully. I can log in to the other machines, but is this altso possible when I am in a different country eg.? how would one connect to a remote host? and how on earth do I copy a file from that machine to this machine? would it be something like cp "filename" "this host" "filename"  ... no right?
I know, I should read the documentationIn order to access these computers from the outside world, you could need to forward port 22 with your router.  In order to copy a file, you can drag and drop files from the graphical interface.

---

### Post by ugm6hr on 2009-05-29
I agree, SSH is the simplest way to achieve this.

However, it will be a lot easier if you have fixed IP addresses for each computer; this can be achieved by setting assigned IP's from your router with DHCP (if your router has that capacity, as most do), or using static IP on your LAN rather than DHCP.

Similar results can be achieved with SMB or NFS too, albeit with less simplicity with Gnome.

An alternative is giver: 
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=giver](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=giver)
[http://code.google.com/p/giver/](http://code.google.com/p/giver/)
However, this is designed to send files, rather than access remotely.

---

