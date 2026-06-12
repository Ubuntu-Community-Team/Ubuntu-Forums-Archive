---
title: "NFS File Permissions coexisting with Samba"
date: 2008-12-29
forum: General Help
---

### Post by Gamzarme on 2008-12-29
Hello. I am attempting to set up a [FreeNAS]("http://www.freenas.org") NFS and Samba file server and I cannot for the life of me figure out how to make it so every file is *not* owned by user **root** and group **wheel**.

This seems to be the default owner and group of any disk that is mounted within FreeNAS. This is okay with me as long as I can still mount the NFS share over my network from my Ubuntu computers. I use the fstab file to do this mounting at start-up with the entry:
```
192.168.0.11:/mnt/Disk0 /home/thomasp/Public nfs rsize=8192,wsize=8192,rw,hard,intr 0 0
```

Of course this then mounts the NFS share with the user **root** and group **root**, a group of whom my Ubuntu computer users are a part of. Of course this means that every file that I place onto the NFS share from Ubuntu gets the permissions of ```
-rw-r--r--
``` which is totally incompatible with my Samba shares but readable with each Ubuntu computer.

I also mount the file server Samba shares from a Windows computer and it does not allow me to access or edit the files copied to the file server from the Ubuntu computers.

My question is this:  is it possible to allow all computers to seamlessly share files with one another over a combination of NFS an SMB?

Some solutions might be:
[LIST]
[*]Force a common group (**family**, for instance)that is applied to each directory or file created from the Ubuntu boxes that would also be accessible from the Samba shares.
[*]Have Samba allow each connected computer to access and edit directories and files stored under the **wheel** group.
[/LIST]

If anyone needs some additional information, I would be happy to provide. Thanks for all of you guys' help! =)

Regards,

Patrick Thomas

---

