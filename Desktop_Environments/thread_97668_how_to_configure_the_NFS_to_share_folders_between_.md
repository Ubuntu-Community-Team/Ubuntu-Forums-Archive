---
title: "how to configure the NFS to share folders between two ubuntus?"
date: 2005-12-01
forum: Desktop Environments
---

### Post by cyberideias on 2005-12-01
I know that I must use the NFS to share folders in linux computers. :rolleyes: 

I have aparently installed the basics packages of the NFS, however I do not have ideia of as I must connect and share the folders. :???: 

how I will be able to have access the folders in other computers?  ](*,)

---

### Post by wrtrdood on 2005-12-01
NFS requires the server side to export the mount points specifically.  Check out **exportfs**.  You have the ability to limit access to specific machines and even specific users.  You'll need to edit the /etc/exports file to allow other machines access.  This is the server part which is on the machine with the resource you need access to.

Clients will then need to have a mount point created where you then connect to the remote using the **mount** command.  For example, I keep a directory of all my MP3s on my server and mount that directory on my laptop using:

  *sudo mount -t nfs server:/home/MP3*

Then, as far as the laptop is concerned, /home/MP3 is a local directory.

Of course, you can also place the root of the drive and export the entire thing but I don't recommend that.

If you're looking for a simple "start the software and everything's there" you're not going to find that.  Even using Samba would take some setup.

---

