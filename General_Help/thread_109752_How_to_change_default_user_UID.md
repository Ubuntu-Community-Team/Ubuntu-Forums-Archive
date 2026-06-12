---
title: "How to change default user UID?"
date: 2005-12-29
forum: General Help
---

### Post by Zill on 2005-12-29
I have just installed Ubuntu 5.10 and my default user UID/GID is 1000.  I need to network this PC with another, running Mandriva, where my default user UID/GID is 500.

As I use basic NFS to connect the two PCs, this requires both PCs to have identical UIDs.

Could anyone please advise how I can (easily!) change all instances of the Ubuntu UID/GID 1000 to 500, ensuring that all config and data files containing this number are updated correctly.  I also need to ensure that all future files will have the correct new UID/GID of 500.

Many thanks,

Zill

---

### Post by schilcha on 2005-12-29
First, edit the files determining the UID and GID: /etc/passwd and /etc/group. Change the UID for the user from 1000 to 500 and the GID for the group with the same name to 500 as well (if such a group exists in mandriva). For the syntax of these files see "man 5 passwd" and "man 5 group".
Then, since UID 1000 and GID 1000 do no longer exist, you need to change the owner of files owned by UID 1000 or GID 1000 to 500. To do this, I'd use "find / -uid 1000" and "find / -gid 1000".  There's an exec-parameter to find, which you can use to change ownership of each file found using chown and chgrp. 
I guess you should not have too many problems afterwards -- one never knows. 

Good Luck!

---

### Post by Zill on 2006-01-02
Thanks for the info schilcha.

I eventually used usermod and chown to change the files and it seemed to work OK.  Not sure if I will find any "funnies" later though ;-)

Thanks again.

Zill

---

### Post by underpope on 2006-01-06
I tried this myself, actually, but ended up losing sudo access for my default user account; I had to boot into recovery mode to fix the issue, and then rechown and rechgrp all my files.  Is there a safer way?

---

### Post by freerick on 2007-05-20
I know this is an old post, but I think that a lot of people have the same issue. I ran into this problem when I tried to access my main PC from one of my other PCs, (both running Ubuntu) via NFS; my user *name* exists on both, but the uids are different on each machine.
Instead of potentially compromising my system by manually editing uids in the /etc/passwd and /etc/shadow files, I'm going to attempt to use the "map_daemon" option of the NFS exports on the NFS server machine and the ugidd command on the client to map my user IDs from server to client dynamically.
More information can be found on 
```
man exports
```
or at [http://man.he.net/man5/exports](http://man.he.net/man5/exports).

---

### Post by freerick on 2007-05-20
update: you need to install the **nfs-common** package (on the client at least, but maybe on the server also) in order for this to work properly in ubuntu with NFSv4. That package provides **rpc.idmapd** (NOT imapd!), which will be used to map user names on the client to user names on the server by way of the uid stored in the /etc/passwd files. This is necessary if the client and the server use different passwd files.

Further, you need to edit your **/etc/exports** file: you need to change the option **squash_all to no_squash_all**. The squash_all option next to your export tells the nfs server to map all incoming mount connections to the "nobody" user, which effectively means that the permissions set for "others" will apply to all files that are remotely mounted, from the perspective of the mounting client, regardless of the client's user name on the client machine and regardless of how it is mapped.
Further, as you may have guessed, even if you follow the method specified in the previous post regarding using 'find [...] --exec [...]' you still won't be able to get full read/write access to your NFS shares from your client machine if the squash_all option is on. Again, I defer to exports(5), which explains these access control options.
If you have set all this up correctly, and you specified rw in your exports file for all shares that you want to mount read/write, you should be able to write to your NFS mounts now. Further, I would highly recommend using some sort of access control mechanism for your incoming connections; while it is my understanding that rpc.idmapd does have some built-in security features, I am not familiar with them and therefore you should grant access only to hosts that you trust. I have implemented this using the **/etc/hosts.allow and /etc/hosts.deny** files, but there are other methods as well, such as iptables.

---

### Post by swampy5 on 2008-01-18
Thanks to those that put me on the right track here - I couldnt work out what weird things were happening to file permissions using nfs from my server to 3 gutsy workstations - have synced all the uids and gids now so all should be sweet from now on. And I did go down the manual path - using the find command with the exec parameter worked best for me when using ssh from another workstation rather than directly on the workstation where I was changing group and ownership. I must check the nfs howto to see if that info is in there. Wonder if it worked by remapping the uids and gids using the exports file on the server.
regards
swampy

---

