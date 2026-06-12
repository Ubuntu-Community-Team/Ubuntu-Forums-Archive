---
title: "Any better way to &quot;map network drives&quot;?"
date: 2009-03-09
forum: General Help
---

### Post by edmicman on 2009-03-09
I'm on Ubuntu 8.10.  I'm also running a FreeNAS install on a spare PC as a file server, with shares via SAMBA (I think...whatever is the default).  Awhile back I finally set up a permanent /mnt mapping by using an entry in fstab to mount the file share, and everything has worked fine.  Until yesterday.

We had a power outage, and my FreeNAS machine shut off.  I was working on my laptop, and wanted to browse to a folder on my filesystem, but could not open any Nautilus explorer window.  No matter what I tried (Computer, Home, subfolders via bookmarks wthin my home folder, etc.), the cursor would just spin busy for a minute and nothing would happen.

I saw in my logs files that there were a bunch of CIFS errors happening, related to my /mnt/ folders.  I went downstairs, turned on the file server, and everything worked again on my PC.

Sooooo....is this really how it's supposed to work?  Aside from the initial issue of it being a royal PITA to map a network share in the first place (why do I have to still edit fstab and find out the syntax, etc??), if that network share isn't available will it really hose my whole file browsing experience?  Why doesn't it try to connect to the share and then timeout after a short while, displaying the rest of filesystem (the local filesystem, which is all I was after in the first place) even if the network is unavailable?

Do I still have something configured wrong?  Do I have the network shares mapped wrong?  I'm not at the PC right, now, but I can paste my fstab line when I get home.  But I just modeled it off a post from these forums in the first place.

Thanks for any info!

---

### Post by albandy on 2009-03-09
you can use pam_mount to use user credentials to automount the share  or mount it throught the desktop option places --> connect to server

Using fstab to automount windows network shares it's not a good idea.

with pam_mount you can choose optional or required so if is set to optional only will mount it if has network access.

---

### Post by edmicman on 2009-03-09
Thanks for the info!  I was using "connect to server" originally, but that didn't seem to be permanent?  Maybe I was doing something wrong, but I was looking for a way to mount network shares always, and have them remembered if I had to restart.  It seemed like when I used the GUI method it would mount it fine, but forget the settings once I rebooted.

I'll check out the pam_mount thing.  Thanks!

---

### Post by jocatoth on 2009-03-09
i also use a freenas box for several computers to store and access (xp pro, xp home, pcbsd and several hardy herron boxes).

in the excerpt from my fastab below the freenas box is Whitebox. its ip is 192.168.1.125. this format assumes desktop folders White_Black, White_Grey, White_White and White_Gold

//Whitebox/Maple	/home/john/Desktop/White_Black	cifs  exec,uid=john,gid=users,ip=192.168.1.125    0    0
//Whitebox/Pine		/home/john/Desktop/White_Grey	cifs  exec,uid=john,gid=users,ip=192.168.1.125    0    0
//Whitebox/Gold		/home/john/Desktop/White_Gold	cifs  exec,uid=john,gid=users,ip=192.168.1.125    0    0
//Whitebox/White	/home/john/Desktop/White_White	cifs  exec,uid=john,gid=users,ip=192.168.1.125    0    0

this also requires the installation of smbfs. hope this may be helpful

---

### Post by jocatoth on 2009-03-09
i just reread your post. my freenas server is very very particular about how it is shut down. if it is shut down without unmounting its drives, it marks those drives for background checks and basically will not respond over the local net. i have found it the quickest to return the server to factory defaults, redefine and remount drives one at a time, and run the fscheck utility singlely as each drive is defined and mounted. with care this can be done without losing the data on the drives. i just go slow and read the screens that freenas provides in the disk management, mounting and cifs tabs.

---

