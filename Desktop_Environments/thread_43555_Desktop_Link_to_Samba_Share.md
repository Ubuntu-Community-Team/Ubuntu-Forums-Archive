---
title: "Desktop Link to Samba Share"
date: 2005-06-22
forum: Desktop Environments
---

### Post by bgfay on 2005-06-22
I have just installed Ubuntu on one of our school computers (incredibly easy, wow). I have a configuration issue:

We have a computer on our network with a shared folder that houses all our students' files. I want a desktop link to that folder. I can navigate to the folder, browse all of the files, and all the rest. 

I am trying to make a link by dragging the networked folder to the desktop and then hitting ALT. This gives me the option to "Link Here" but when I choose "Link Here" I get the following message:

Error "Unsupported operation" while
creating a link to "smb://(location of the share)

What am I doing wrong? Thanks.
--
Brian

---

### Post by intangible on 2005-06-22
Try right clicking on the share and selecting "Connect to this Server" then for Link Name put what you want it to be called.

If you want to map to a sub-folder, you'll have to use **Places->Connect to Server** and then fill out the proper information.

Yeah it's not that intuitive, but it works, and I expect it to get better.

You could also look into installing smbfs and then using **mount** to map the drive directly, it would then act like a normal directory.

[http://ubuntuforums.org/showthread.php?t=42486&highlight=smbfs](http://ubuntuforums.org/showthread.php?t=42486&highlight=smbfs)

---

### Post by bgfay on 2005-06-22
I have been trying to use this method:

[http://ubuntuguide.org/#automountnetworkfoldersall](http://ubuntuguide.org/#automountnetworkfoldersall)

But I can't figure out a couple of things. It assumes the following:

[B]Assumed that network connections have been configured properly
     Network computer's IP: 192.168.0.1
     Network computer's Username: myusername
     Network computer's Password: mypassword
     Shared folder's name: linux
     Local mount folder: /media/sharename[/B]

Alright, which computer is the Network computer? Is it this Linux machine from which I'm trying to access the share or the Windows computer on which the share resides? I have been assuming that it is the Linux machine. 

Also, the shared folder's name is, I assume, the name of the file on the Windows computer. Do I need to include a path to it? 

I ask, because when I do sudo mount -a, I get the following message:

mount: wrong fs type, bad option, bad superblock on //ipaddress/Shared
          missing codepage or other error
          In some cases useful info is found in syslog - try
          dmesg | tail or so

Any thoughts?
--
Thanks, 
Brian

---

### Post by intangible on 2005-06-22
OK, here is some simplified instructions I gave to someone else, it should help: [http://ubuntuforums.org/showpost.php?p=217876&postcount=2](http://ubuntuforums.org/showpost.php?p=217876&postcount=2)

You should be able to see the items to customize to you without any problem.

Let me know if anything is too confusing there and I will explain.

---

### Post by intangible on 2005-06-22
[QUOTE=intangible]OK, here is some simplified instructions I gave to someone else, it should help: [http://ubuntuforums.org/showpost.php?p=217876&postcount=2](http://ubuntuforums.org/showpost.php?p=217876&postcount=2)

You should be able to see the items to customize to you without any problem.

Let me know if anything is too confusing there and I will explain.[/QUOTE]

Oh yeah, and to make the mount stay through a reboot:

**sudo gedit /etc/fstab**
and put in this line (modified to your setup of course:
```
//server/share   /remote   smbfs   username=tridge,password=foobar,uid=1000,gid=1000  0  0
```

---

### Post by bgfay on 2005-06-22
I'm still getting the same error message about wrong fs type. 

I can see the network share, I can access it, I can do everything. All I want is to make it so that I don't have to go through so many mouse clicks to get there.

The share is on an XP machine if that matters.
--
Brian

---

### Post by bgfay on 2005-06-22
Thank you!

---

