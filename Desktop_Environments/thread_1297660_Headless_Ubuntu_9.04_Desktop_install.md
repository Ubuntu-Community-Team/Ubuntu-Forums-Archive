---
title: "Headless Ubuntu 9.04 Desktop install"
date: 2009-10-22
forum: Desktop Environments
---

### Post by ssjgoku24 on 2009-10-22
Hey guys, 

This is my first post here. I'm not completely new to ubuntu but I'm no pro.

So here is the situation. I have a server that is in a data center that I cannot physically access, aka it is headless. I wanted to be able to remote into the server somehow to use the gui for random things. Now I tried installing an NX server from no machine I installed the client, node, and server for it on ubuntu, I also configured it and it starts fine on ubuntu. Now the problem is when I try to remote in using my windows computer and the client for it. 

Here is the error I get.

```
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: E1D94A41. To get detailed information about
NX> 595 ERROR: the error search for the string E1D94A41 in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Exiting on signal: 15
```

I cannot for the life of me figure out what it is. I tried locating that log but it is empty.


Thanks guys!

---

### Post by arcull on 2009-10-22
Hm, looks a bit strange, never had such an issue with nx. Did you generate the default key DSA key and used it on the windows machine? The generated file should be located in /usr/NX/share/keys/ ,although this may depend on the version of the nx server you use. So the file in there usually has the name default.id_dsa.key, this file you should use when connecting from the remote windows machine. If you already did this correctly, and still doesn't work, I would try to connect from windows machine to the host machine via putty [http://www.chiark.greenend.org.uk/~sgtatham/putty/]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/")  just to make sure the ssh connection which is the protocol nx uses, can be establised. If it doesn't there may be somehing with the network the cause of the problem

---

