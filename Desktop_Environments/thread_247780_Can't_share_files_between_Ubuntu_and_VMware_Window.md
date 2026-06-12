---
title: "Can't share files between Ubuntu and VMware Windows XP"
date: 2006-08-31
forum: Desktop Environments
---

### Post by abelthorne on 2006-08-31
I have installed VMware Server using the how-to found on this forum. It works fine, but I'm unable to share folders/files between the host (Ubuntu) and the VM (Windows XP).

I have set up a shared folder Ubuntu-side with the Samba protocol and in the "Workgroup" network group (same as Windows-side) and I can't see it in Windows. I can see the Windows virtual computer in its own group but nothing else. Internet access works in Windows.

I think it may come from my network configuration and I'm not really competent with this.
I have an internet connection with an ethernet modem that is connected to my computer (i.e. for French users : my provider is Free and I have a Freebox v3). Thus, in network settings in Ubuntu, the eth0 has the internet IP address set to me by my provider.
VMware server has set up vmnet1 (192.168.253.1) and vmnet8 (192.168.65.1).
My ethernet card (eth0) is set to DHCP (I think it is needed for my internet connection).

What should I set and how in order to have network between Ubuntu and VMware Server ?

---

### Post by cebesius on 2006-08-31
If you have XP Pro:

On your Windows XP virtual machine, open up Explorer -> Tools -> Folder Options -> View tab and disable simple file sharing.

In Ubuntu, point the folder location to smb://yourwindowsVM/c$ and login with the Administrator password from Windows.  You should be able to read and write.  I don't think this will work for XP Home.

---

### Post by abelthorne on 2006-08-31
This doesn't seem to work : Ubuntu can't find the virtual PC and Windows still only finds itself in the network neighborhood.

---

### Post by galileon on 2006-09-05
hiya

i was using zonealarm in windoze xp vmware, which was stoping my ubuntu from getting to the network share..

zonealarm gave me an ip, 172.41.xxx.1, which was the ubuntu vmware server,

so i added this address  as a trusted domain, and my samba<-->woes net neighbourhood works great now...

are you using a firewall?

---

### Post by abelthorne on 2006-09-05
The Windows XP SP2 firewall is on. I'll try to turn it off and see if network access works better (although I'm not that happy to switch the firewall off on a Windows PC that has access to the internet).

---

### Post by galileon on 2006-09-05
lmao, yeah, thats why first thing i do is install zone alarm off a cd, then update as soon as the net works...
btw i dont even trust the M$ firewall, thats why i use ZA

---

