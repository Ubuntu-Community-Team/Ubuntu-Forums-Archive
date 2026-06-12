---
title: "Is my ssh secure?"
date: 2009-01-07
forum: General Help
---

### Post by Tactical Fart on 2009-01-07
I'm aware that there are two types of ssh, protocol 1 and 2. The first is plain text and can easily intercepted and read. The second, not so much. I followed two different walk-throughs for setting up keys. One resulted in a "authorized_keys" (which is what I'm sure the computer is using) and used
```
$ ssh remoteuser@remotehost
remoteuser@remotehost's password:
remoteuser@remotehost:~$ cat id_rsa.pub >> ~/.ssh/authorized_keys
remoteuser@remotehost:~$ rm id_rsa.pub
remoteuser@remotehost:~$ exit 
```

The other used authorized_keys2 and id_dsa, but a similar procedure.

I made sure that /etc/ssh/sshd_config has a line that reads
```
Protocol 2
``` and not ```
Protocol 1,2
```

I'm using the correct protocol, right?

---

### Post by jgoguen on 2009-01-07
SSH protocol 1 isn't plain text, it's encrypted.  IMO, protocol 2 is definitely the one to use though, and using **Protocol 2** in sshd_config will make sure the server only accepts SSH protocol 2.  For Ubuntu, your authorized keys file should be ~/.ssh/authorized_keys.  Here's how I set up my public-key auth between two Ubuntu boxes, odin (client) and thor (server):

[list]
[*]On odin, run **ssh-keygen -t rsa -b 4096** - this results in, by default, ~/.ssh/id_rsa and ~/.ssh/id_rsa.pub
[*]Copy ~/.ssh/id_rsa.pub from odin to thor and append to ~/.ssh/authorized_keys on thor.  id_rsa.pub can be removed from thor now.
[*]On both boxes, run **chmod -R go-rwx ~/.ssh/** to make sure permissions are set properly.  If permissions are wrong, it doesn't matter whether it's set up right or not, sshd won't use public key auth.
[/list]

There's also changes to */etc/ssh/sshd_config* on the server side (restarting sshd after making changes) which you've gotten right.

Note that in my method above, you could replace "rsa" with "dsa" by running **ssh-keygen -t dsa -b 1024** (since DSA keys must be 1024 bytes) and using id_dsa and id_dsa.pub instead of id_rsa and id_rsa.pub.

HTH

---

### Post by whoop on 2009-01-07
yes, sir.

#Protocol 2,1
Protocol 2

---

