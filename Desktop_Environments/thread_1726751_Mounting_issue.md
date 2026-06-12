---
title: "Mounting issue"
date: 2011-04-11
forum: Desktop Environments
---

### Post by cscj01 on 2011-04-11
I have recently had a hard drive go bad.  I had a current backup on an external USB hard drive on an XP machine on my home network.  I use luckyBackup to back up the disk on a regular basis.  In order to do this, I would mount the USB drive on the XP machine to my local Ubuntu machine at /mnt/cp2 with the command
```
sudo mount /mnt/cp2
```
Then my luckyBackup script would execute.

In order to copy my backup to my new hard drive in the most efficient manner, I attached the USB backup drive to my Ubuntu machine and copied the contents of the backup drive to the new hard drive.  I then moved the USB drive back to the XP machine.  I checked all the share properties on the USB drive on the XP machine, and, where necessary, reset them to share the drive.

Herein lies the problem.  I can no longer mount the USB drive locally.  When I issue the command
```
sudo mount /mnt/cp2
```
I get the following message:
```
Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

I can access the USB drive by going through Places>Network>CP2, but luckyBackup seems to require it be mounted locally.  The /mnt/cp2 folder is present in my file system.

Any ideas?

---

### Post by cscj01 on 2011-04-12
bump

---

### Post by cscj01 on 2011-04-13
bump

---

### Post by Gnofwarwick on 2011-04-14
By unplugging the USB drive, you have likely created a different mount point when it was plugged back in - that's not a problem nor a fault.

after you have connected to the external drive as normal using the Places/Network, then drop to the command line and type ls -ltu /mnt/ and look for a mount point that it newer (in time).

Then sudo mount /mnt/<new dir> as normal

---

### Post by sapavietnam on 2011-04-14
Canonical and Ubuntu

 
As the leader of the Ubuntu Project, Canonical knows Ubuntu inside out.

Working with a close-knit team from the open-source community, Canonical is responsible for delivering six-monthly releases, as well as co-ordinating security, trouble-shooting and providing an online platform for community interaction.
 
The number-one provider of Ubuntu services, Canonical works closely with businesses and individuals alike. Canonical also develops bespoke systems, provides comprehensive support and all the training that’s necessary to get everybody up and running. With more than 300 employees in over 18 countries, the company continues expanding to support the millions of Ubuntu users around the world.
[sapa vietnam hotel]("http://www.sapavietnamhotel.com /")-[vietnam tours]("http://www.toursvietnam.org /")-[vietnam travel]("http://www.travelagentvietnam.org/")

---

### Post by cscj01 on 2011-04-14
> **Gnofwarwick said:**
> By unplugging the USB drive, you have likely created a different mount point when it was plugged back in - that's not a problem nor a fault.

after you have connected to the external drive as normal using the Places/Network, then drop to the command line and type ls -ltu /mnt/ and look for a mount point that it newer (in time).

Then sudo mount /mnt/<new dir> as normal

Thanks for your response.  Here's the result of your suggestion:
```
ls -ltu /mnt/
total 4
drwxr-xr-x 3 root root 4096 2011-04-11 12:13 cp2

```

I am not sure what this tells me except that the mount point cp2 exists in /mnt.  In Places>Network, I have cp2.  In cp2, the drive shows as > Data(g) and in properties the location is > smb://cp2/  I believe this means it is a Samba share.  If I try to mount it, I get the message in my original post, ```
Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```
If I unmount the Samba share > Data(g) on cp2 and try to mount the drive, I get the same error.

Perhaps this has something to do with the sharing options I have set on the drive on the XP machine?

I believe before this adventure began, the drive showed as > g on cp2 rather than as > Data(g) on cp2  Does this indicate something significant?

Thanks again for your help.

---

### Post by cscj01 on 2011-04-15
bump

---

### Post by cscj01 on 2011-04-15
> **gzal37577 said:**
> The problem with mounting WITHIN the wall is that the heat has nowhere to dissipate.

If you look at the back of the set, it probably has lots of vent holes for internally generated heat to esacpe

Duh?

This problem is resolved.  The share name > Data(g)on the XP machine was reset to the default when I re-attached the drive.  Before it had been > g  When I reset the share name to g and issued the command```
sudo mount /mnt/cp2
```it mounted locally.

I am still not sure where I should look to see where the values are stored (i.e., /etc maybe) that relate to local mounting of samba shares, but the problem of being able to back up my data using luckyBackup is solved.  Thanks again, Gnofwarwick.

---

