---
title: "Nautilus times out when trying to mount SFTP share"
date: 2009-12-20
forum: Desktop Environments
---

### Post by mangoHead84 on 2009-12-20
Hi,

I have a server (CentOS) on which I allow passwordless root login (using public key authentication). I can connect to this server without a password just fine from the command line using 'ssh root@[server ip]'. 

However, when I try to go 'Places'->'Connect to Server...', enter the credentials etc.... I get an error saying 'Cannot display location "sftp://root@[server ip]/". Timed out when logging in'

The latency between my desktop and the server is quite high, so I can understand why the timeout happens, but I was wondering where I could change this timeout variable?

I believe it should be changed under '/usr/share/gvfs/mounts/sftp.mount', but there's no documentation on the variables and/or parameters which are allowed in this file and which format they have to be in. I've tried googling for answers and also tried to find documentation on the main gvfs site, but to no avail.

Does anyone know where you can change the sftp log in timeout for the gvfs-sftp backend? And through this prevent Nautilus from throwing the 'Timed out when logging in' error?

Thank you

---

### Post by Lars Noodén on 2009-12-21
> **mangoHead84 said:**
> Hi,

I have a server (CentOS) on which I allow passwordless root login (using public key authentication). I can connect to this server without a password just fine from the command line using 'ssh root@[server ip]'. 


When you connect via the shell, how are you loading the key and how are you loading the passphrase for the key?  

```

# manually during the connecton
ssh -i ~/.ssh/key *centos-server.example.org*

# pre-loading with an agent
ssh-add ~/.ssh/key

```

Also, what problem are you trying to solve with allowing root login?  There is probably a safer way to do the same task.

---

### Post by mangoHead84 on 2009-12-21
I've pre-generated the key and put it under the default '~/.ssh' directory. The private key is not stored encrypted so it does not ask for a password. 

The problem I'm trying to solve is that I am trying to setup and configure this machine and would like to mount its filesystem as a directory, so that I can work with the configuration files (under '/etc') as if they were local files. 

As for this method being unsafe, I thought that as long as my private key was kept safe, the security was just as safe as password login.

---

