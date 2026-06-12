---
title: "nomachine nxclient ssh error -  but ssh works?"
date: 2009-01-03
forum: General Help
---

### Post by onko on 2009-01-03
I installed the three packages from nomachine

nxclient_3.3.0-3_i386.deb
nxnode_3.3.0-3_i386.deb
nxserver_3.3.0-8_i386.deb

added the line
```
AuthorizedKeysFile /usr/NX/home/nx/.ssh/authorized_keys2
```
into /etc/ssh/sshd_config

and opened in my router and via firestarter everywhere the port 22!

If i try from my Windows client to connect to my server via putty, it works! So i can be sure that ssh works and that means that the port 22 is open!

But if i try to connect with my nxclient i get
```

NX> 203 NXSSH running with pid: 2684
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: **.***.**.*** on port: 22: Connection timed out

```

Any idea?

Greetings

---

