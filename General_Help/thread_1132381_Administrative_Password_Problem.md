---
title: "Administrative Password Problem"
date: 2009-04-21
forum: General Help
---

### Post by Mel Shepherd on 2009-04-21
I am having problems getting my internet connection to work.  I am using VMware Workstation 6.5 and the error message says, "the network bridge on device VMnet0 is not running. The virtual machine will not be able to communicate with the host or with other machines on your network. Failed to connect virtual device Ethernet0. 

So, I try using the line commands that VMware explained to someone else and my administrative password will not work.  How do I solve this problem?  I am into forum from my Vista Ultimate 64 bit series.  Please help someone! 


,,,,,,,,,,

---

### Post by Yellow Pasque on 2009-04-21
It depends on what commands you're using. Remember that the root account is disabled on Ubuntu for security reasons. For a root terminal, you can use this command:
```
gksu /usr/bin/x-terminal-emulator
```

---

