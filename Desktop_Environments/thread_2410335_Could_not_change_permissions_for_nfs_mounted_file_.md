---
title: "Could not change permissions for nfs mounted file when copying with Dolphin"
date: 2019-01-14
forum: Desktop Environments
---

### Post by lothian53 on 2019-01-14
Hi, I am running FreeNAS 11.2 as a server and have Ubuntu 18.04 installed in a virtual machine on the server. I have mounted several nfs drives from the freenas server onto the VM. I have a user that has the same UID and GID on both machines and from the command line, I can copy or move files just fine. However when I use Dolphin try to copy a file from one NFS folder to another, I get an error saying "Could not change permissions for '/mnt/videos/foo'. The file (foo) actually gets copied and is there in the destination folder. The file foo in the destination folder has the same permissions as it had in the soruce folder.

I thought that perhaps there was some root access happening so I set up the exports as follows on the FreeNAS server:

/mnt/Riverdale/shares/videos -maproot="root":"wheel"
/mnt/Riverdale/shares/public/files -maproot="root":"wheel"

Now I can  use root to change ownership of files and folders but my problem with Dolphin remains. I don't understand why it is trying to play with the permissions.

Can somebody point me in the right direction?

PS: the root on the client has exactly the same gid and uid, (972:0)   however the name of the group is different. On the client it is "plex:root" but on the server it is "plex:wheel". but the UID/GIDs are the same on both.

---

### Post by TheFu on 2019-01-14
And use of uid 0 (zero) from a remote system on NFS storage is blocked by default by NFS.  This is a security consideration.  In short, don't use a uid of 0 for anything NFS.

Ok, but sometimes you and I know better and must use a uid of 0 for "reasons", so NFS has an export option to allow it,
no_root_squash.  Put that option into the exports file for each export where you want to allow remote root to be used.  From the manpage:
```
       root_squash
              Map requests from uid/gid 0 to the anonymous uid/gid. Note  that
              this  does  not  apply  to  any other uids or gids that might be
              equally sensitive, such as user bin or group staff.

       no_root_squash
              Turn off root squashing. This option is mainly useful for  disk&#8208;
              less clients.
```

Or did I completely misunderstand?

---

### Post by Skaperen on 2019-01-16
where you are copying to, on the machine doing the copying, is that file on a local filesystem or is it on a remote filesystem that this machine accesses using NFS?  i'm just not getting a mental picture of the setup you are doing this on?  does the machine doing the copying any local disk space or is it a diskless machine?

---

### Post by lothian53 on 2019-01-16
It happens even if it is just a subfolder of the original folder. Note that I can do this from the command line just fine. This only happens when I use the file manager (Dolphin) to copy files. If I copy the files using the command line then there are no problems. With experimentation, I know that I cannot change the permissions on any files in my NFS mount. And for some reason the file manager likes to toy with the permissions after the file is copied.

---

### Post by lothian53 on 2019-01-17
I think I have it figured out. I was being blind to the conditions. These same NFS shares are also on CIFS. And there are Windows ACLs on the folders. So when I create a brand new dataset with no Windows ACLs on it, things work great. Thanks for your ideas. I should have given the whole store about the other shares. I had read that there were no problems with NFS and CIFS shares on the same data, but obviously, there are conditions for that!.

---

