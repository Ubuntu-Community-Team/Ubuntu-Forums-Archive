---
title: "NAS - Lacie Ethernet Mini Disk - How do I mount it?"
date: 2009-01-20
forum: General Help
---

### Post by nashienet on 2009-01-20
Hi all,

I have read a few different pages on the web about mounting NAS drives but I haven't been able to sort out my own because I'm not entirely sure on how the solutions work - so I'm not sure on what I'd need to change in fstab in order to get it working properly.

First of all I can mount my NAS drive fine in Nautillus (I've defined it as a windows share (if I hover over the bookmark it says 'smb://admin@192.168.2.5/mediadrive/' - how do I translate this into a line of code to put into fstab?

I've been going through this thread:

[http://ubuntuforums.org/archive/index.php/t-441642.html](http://ubuntuforums.org/archive/index.php/t-441642.html)

But the problem is I don't understand how to write a line in the right format, because I don't understand quite what's going on in the examples in that thread.


\\192.168.1.152\PUBLIC /mnt/nas_disk smbfs user,defaults 0 0

For example - if I altered that for my own NAS drive, I would have guessed it would be:


\\192.168.2.5\mediadrive /mnt/nas_disk smbfs user,defaults 0 0

In the above line I've got the location of the drive, then the folder on the local system where I want the drive mounted, then presumably 'smbfs' is declaring that its using samba? then presumably user should be replaced with 'admin'? what does default do, and what does the 0,0 do? and where do i pass in the password? (which is just admin - its available to all users on my network)

Any help or clarification would be greatly appreciated?

---

### Post by dcstar on 2009-01-20
> **nashienet said:**
> 
.........
\\192.168.2.5\mediadrive /mnt/nas_disk smbfs user,defaults 0 0

In the above line I've got the location of the drive, then the folder on the local system where I want the drive mounted, then presumably 'smbfs' is declaring that its using samba? then presumably user should be replaced with 'admin'? what does default do, and what does the 0,0 do? and where do i pass in the password? (which is just admin - its available to all users on my network)

Any help or clarification would be greatly appreciated?

"user" is not to be touched, it is an option to allow normal users to mount and unmount the device.

```
man mount
``` shows you all the options used in an fstab file.

---

