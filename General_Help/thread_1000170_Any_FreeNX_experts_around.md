---
title: "Any FreeNX experts around?"
date: 2008-12-02
forum: General Help
---

### Post by bankie on 2008-12-02
I've recently setup the FreeNX Server on one my Ubuntu boxes with the intention of remotely logging in to my home PC from work. I'm getting a "Connection timeout" message when I attempt to connect. I can connect ok from the local machine.

SSH is setup on port 443 and I can login with no issues. I've uncommented and set Port 443 in the server and node.conf files.

The client error log:
```

NX> 203 NXSSH running with pid: 4140
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: xxx.xxx.xxx.xxx on port: 443
Warning: the RSA host key for '[xxx.homelinux.net]:443'
differs from the key for the IP address '[xxx.xxx.xxx.xxx]:443'
Offending key for IP in /cygdrive/c/DOCUME~1/BANKIE/.ssh/known_hosts:2
Matching host key in /cygdrive/c/DOCUME~1/BANKIE/.ssh/known_hosts:3
Are you sure you want to continue connecting (yes/no)? 
```

It looks like it may have something to do with the keys but I'm currently using the ones that are included.

Thanks

---

### Post by bankie on 2008-12-02
I managed to get it working 10 minutes after making the original post.  :mad:

I just needed to go to the Documents and Settings\Username\.ssh and delete the known_hosts file. After I deleted I was able to start the client and it connected on the first try.

---

