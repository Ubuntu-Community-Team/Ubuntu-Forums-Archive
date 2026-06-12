---
title: "Lost Symlinks with NIS and NFS"
date: 2009-02-14
forum: General Help
---

### Post by M70JRD on 2009-02-14
Hi, I'm relatively new to Linux and I'm stuck.

I have Ubuntu server which, serves up my webpage, mail etc. It also acts as a file server. On my home network are a Ubuntu client machine, an Xbox and a laptop.(The laptop is windows but I desperate to move Linux once this problem is solved)
The server is running NIS, which took me a while to sort, however this is working well.I have several users and their files are in /home/users/name
My media files are in a mount /media/Disk4/music. To give the users access to the files I created a symlink to the files, this works on the server.

THE PROBLEM: when I loggon to the client machine I see all my files, but my symlinks don't work.

Has anyone any ideas please

---

### Post by heindsight on 2009-02-14
NFS doesn't interpret symlinks - it just treats them as normal files. The client machine interprets the symlink and tries to dereference it within it's local filesystem tree. Also, if the link doesn't point to some location within an NFS exported directory tree, the client would have no way of accessing the target of the link anyway.

You'd be better off using 
```
mount --bind /media/Disk4/music /home/users/name/music
``` for each user, or something similar.

EDIT:
Or, if your NFS server is exporting /home/users you could also do 
```
mount --bind /media/Disk4/music /home/users/music
```
and then make a relative symlink pointing to ```
../music
``` inside each user's home directory. Having a relative symlink pointing to a location within the same exported tree shouldn't cause any problems.

---

### Post by M70JRD on 2009-02-14
Thanks for that, this works on the server I can browse all the sub folders and ultimately the MP3s. However when I'm on the client as a user I see the top level folder ie /home/users/john/music but not all the subfolders.
Am I missing something basic, I don't know somthing like /* ???
By the way I'm browsing the server with admin rights, not sure that has any implications.

Thanks

John

---

### Post by heindsight on 2009-02-16
My mistake. Just binding /media/Disk4/music to /home/users/name/music or /home/users/music isn't good enough since, by default NFS exports do not cross mount points (have a look at the exports man page). 

One way of dealing with this is to set the crossmnt option on /home/users in /etc/exports on the server. Then your clients should be able to access everything mounted under /home/users[/name]/music. However, the exports manual warns that:
> some NFS clients do not cope well with this situation as, for instance, it is then possible for two files in the one apparent filesystem to have the same inode number. 

So, you might be better of not using ```
mount --bind
``` but simply exporting /media/Disk4/music separately (of course in theory you'd have no guarantees about where the client will be mounting it, so symlinks from user home directories could be problematic).

---

### Post by M70JRD on 2009-02-16
I took you first idea, and looked at it slightly differently. I mounted the Server NFS share to the same mount point on the client, this resolved the missing links. This allowed for all the files to be accessed.
I now mount the NFS share via /etc/fstab
I couldn't get the relative mount to work but i'll give it another try.

The wife and kids now have access to the shares no matter which machine they get on, excellent.

Many thanks for the idea:)

John

---

