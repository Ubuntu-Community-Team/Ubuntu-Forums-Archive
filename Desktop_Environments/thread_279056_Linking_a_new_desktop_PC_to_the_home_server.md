---
title: "Linking a new desktop PC to the home server"
date: 2006-10-17
forum: Desktop Environments
---

### Post by andersja on 2006-10-17
Hi there,

I have a home server currently set up with Dapper and I've bought a new desktop PC I'm going to run the latest Edgy beta on. 

I want the desktop PC to take its user authentication from the home server, and I want to automatically mount the /home/{user} from the server.

I've read up the NIS HowTo (old? - it says Warty only), as well as the IPSec Howto:
[https://help.ubuntu.com/community/SettingUpNISHowTo]("https://help.ubuntu.com/community/SettingUpNISHowTo")
[https://help.ubuntu.com/community/IPSecHowTo]("https://help.ubuntu.com/community/IPSecHowTo")

This should explain how to get the user authentication running.

Next: how do I auto-mount from server:/home/{user} to /home/{user} on the desktop?

---

### Post by andersja on 2006-10-17
... also; what is the (ballpark figure) performance impact of IPSec? Does anyone use this in a similar home-setup?

---

### Post by andersja on 2006-10-17
> **andersja said:**
> Next: how do I auto-mount from server:/home/{user} to /home/{user} on the desktop?

And the answer seems to be here:[https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

> The following configuration example sets up home directories to automount off an NFS server upon logging in. Other directories can be setup to automount upon access as well. 

Add the following line to the end of /etc/auto.master: 

  /home         /etc/auto.home
Now create /etc/auto.home and insert the following: 

  *             solarisbox1.company.com.au,solarisbox2.company.com.au:/export/home/&
The above line automatically mounts any directory accessed at /home/[username] on the client machine from either solarisbox1.company.com.au:/export/home/[username] or solarisbox2.company.com.au:/export/home/[username]. 


---

