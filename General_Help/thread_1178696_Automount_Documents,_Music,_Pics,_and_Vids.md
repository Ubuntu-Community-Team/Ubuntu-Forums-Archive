---
title: "Automount Documents, Music, Pics, and Vids"
date: 2009-06-04
forum: General Help
---

### Post by bwlange3 on 2009-06-04
I have recently installed Ubuntu Desktop and Ubuntu Server on 2 separate machines.  I would like to also install Desktop on a laptop.  I want to be able to store Documents, Music, Pictures and Videos on the server to allow access from from either the Desktop of the Laptop.  This seems like a pretty simple task, however I have been searching for weeks for a simple way of doing this and have come up empty handed.  Both the desktop and the laptop connect to the network via wireless connections.

I would like to use automount to do this.  I have tried automounting each users entire home directory to the server and it works fine until I reboot the desktop and then upon login it says the users home directory does not appear to exist (which is happening, I believe, becasue the desktop is not yet connected to the network because it is wireless).  My /etc/auto.home file looked like this...

* 192.168.0.100:/media/export/home/&

So, basically what I am looking to do is to just automount the Documents, Music, Pictures, and Videos directories of all users to the server.

Thanks in advance for any help!!

---

### Post by Celauran on 2009-06-04
NFS or Samba will accomplish this. You can have them automount via fstab. Of course, the machine sharing the files needs to be up first.

---

### Post by bwlange3 on 2009-06-04
Sorry I guess I was not clear enough.  I have NFS set up on both machines (and working).  fstab does not work, because (I think) the desktop is connecting to the network via wireless and is not connected at the time that fstab is executed.  This really seams like it should be a simple thing to do, but nothing (fstab, autofs, etc.) have worked so far.

---

### Post by Celauran on 2009-06-04
Ah, now I get it. Seems like a pretty likely scenario, too. Have you tried creating a shell script to auto mount it? Something along the lines of

```
sleep 60 && mount /whatever /wherever
```

---

### Post by bwlange3 on 2009-06-04
I have kicked around the idea of just creating a shell script (I did write a script that would mount the network shares), but I want it to be automated for other users (my fiance, guests, etc.) who do not know anything about Linux and coming from Windows.  The shell script would have to be run as sudo and therefore would not be automated.  Thanks for the reply though.  Surely someone out there has figured out how to do this...

---

### Post by bwlange3 on 2009-06-05
Still nothing on this.  I can't believe no one has tried to do this before.  It seems like it would be a common issue.

Please help!!

---

### Post by bwlange3 on 2009-06-05
bump

---

### Post by sabre2th on 2009-06-05
Off the top of my head, a quick a dirty workaround would be to have the computer automatically log in to a guest/dummy account at boot to start the wireless.

Seems like you should be able to make it work without doing something like that, but I'm drawing a blank at the moment

Edit: What I do is keep users home folders on the local hard drive, with easy links to server shares for saving things.  That way, you can boot without hassle even if the network is down.  It does save some headaches.

---

### Post by bwlange3 on 2009-06-05
The links are not a bad idea, however I will still have to mount the network shares at boot which is where the real problem comes in.  And I also want all my Documents, Music, etc. to appear in their respective directory because that is where most programs look for those types of files by default (as I said I would like it to be seamless for inexperienced users).  It sure seems that automount should work (and as I said it does, with the entire home directory, until a reboot), but I can't seem to get the syntax correct for just automounting subdirectories.

Is anyone on this board extremely familiar with automount.  I want to automount subdirectories of the /home directory.  For example I want auto.master to be written...

```

/User1 /etc/auto.User1

...or...

/home/User1 /etc/auto.User1

...or...

../User1 /etc/auto.User1

```...and then auto.User1 would be written...

```

/Docuements      192.168.0.100:/media/export/home/User1/Documents
/Music               192.168.0.100:/media/export/home/User1/Music
/Pictures            192.168.0.100:/media/export/home/User1/Pictures
/Videos              192.168.0.100:/media/export/home/User1/Videos

```...but that does not work.  It seems like it should work, but I must be missing something.

When I run - sudo /etc/init.d/autofs status - for all the above examples I get...

> 
Configured Mount Points:
------------------------
/usr/sbin/automount --timeout=300 /home/brady file /etc/auto.brady 

Active Mount Points:
--------------------
Any other suggestions.  Thanks again for the help so far!

---

### Post by Savita Eli on 2009-08-03
Hi,

Were you able to do this?
Even I am facing problems with this kind...
The problem is straight fixed if the nfs shares to be mounted are in single dir..
I mean /home/user1 can get mounted on client in /home/user1.

Any idea on how to automount multi-dir nfs shares onto single dir:
Like On server its: /dir1/dir2/sub.
On client I want it as: /dir1/sub

---

