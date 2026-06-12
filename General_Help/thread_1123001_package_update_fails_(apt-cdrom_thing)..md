---
title: "package update fails (apt-cdrom thing)."
date: 2009-04-11
forum: General Help
---

### Post by Xender1 on 2009-04-11
In the top right corner of my screen on my top panel i see a triangle with an '!' in it. Highlighting it reads: "The update information is outdated. This may be cauesd by network problems or by a repository that is no longer available. Please update manually by clicking on this icon and then selecting 'Check for updates' and check if some of the listed repositories fail." 

so i click that icon and it opens the update manager. and hit check.
it then starts downloading some repository stuff but pops up with an error: "Could not download all repository indexes". 

These are what says failed: 
Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

When i do "sudo apt-get update" from terminal i get at the top of the update it is this:
W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

anyone know how to fix this problem? Thanks so much!

---

### Post by taurus on 2009-04-11
Close down the update manager.  Then, open System -> Administration -> Software Sources and remove the check mark for Cdrom.  Close it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Xender1 on 2009-04-11
solved! thank you very much

---

### Post by Ready2DropWin on 2010-04-18
Hello,

I have tried to use

sudo apt-get update
sudo apt-get upgrade

and I restarted and tried to do update manager and I still get this

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch cdrom://Ubuntu 10.04 _Lucid Lynx_ - Beta amd64 (20100406.1)/dists/lucid/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 10.04 _Lucid Lynx_ - Beta amd64 (20100406.1)/dists/lucid/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

As you can see I am using 10.04 x64 and this issue happened after I updated last night. I am not sure what else to do. Thanks in advance for any help.

---

### Post by tperwez on 2010-04-18
> **Ready2DropWin said:**
> Hello,

I have tried to use

sudo apt-get update
sudo apt-get upgrade

and I restarted and tried to do update manager and I still get this

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch cdrom://Ubuntu 10.04 _Lucid Lynx_ - Beta amd64 (20100406.1)/dists/lucid/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 10.04 _Lucid Lynx_ - Beta amd64 (20100406.1)/dists/lucid/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

As you can see I am using 10.04 x64 and this issue happened after I updated last night. I am not sure what else to do. Thanks in advance for any help.

This is not going to solve your problem but I am having almost identical issues with 9.10 that I upgraded to two days ago. I upgraded from 9.04 with ISO image and the system started to lock up. I tried to run the Update Manager after unchecking the cdrom button and started to get the same kinds of errors and warnings. When I ran

sudo apt-get update

I saw that it downloaded many packages (11.4 MB). However, when I ran

sudo apt-get upgrade

no packages got installed. I got the message that 0 ,packages were removed, o installed etc.

 When I tried to run Update Manager, it still downloads packages but does not install them. It tells me that system is upto date. Then why does it download so many packages? In fact, I can continue to click Check button and every time it fetches the same packages but not install them. Usually,  in the process the system locks up and then I have to do hard boot again. Never had such bad experiences with an OS (not even with the old Mac OS 9). 

Seriously thinking of switching to Red Hat if I have to start with clean install. Ubuntu always seem to be years behind everybody else in updating their repositories despite the fact that they are quick to throw in a new releaase every few months without having tested it properly.

---

### Post by Ready2DropWin on 2010-04-18
Well I am glad that someone else is having the same issue, and its just not me. I know that doesn't help you, but thank you for taking the time and replying back with some info.

---

### Post by broomfighter on 2010-05-01
This is affecting me, too. I tried apt-get update to no avail.

---

### Post by newb85 on 2010-05-17
I was experiencing the same problem myself.

Unless you've already changed one of these settings, what's basically  happening is that NetworkManager is setting your router up as the DNS  server, and the router should use your ISP's DNS server to resolve  addresses.  Somewhere in there, addresses aren't all being resolved  correctly, hence "no address associated  with hostname".   If you want to see what's being used to resolve addresses, open  /etc/resolv.conf

NetworkManager can easily be set up to always use a manually-specified  DNS server when using a given network.  Under "Edit Connections..."  select the network where the issue is occurring (selecting the proper  tab at the top, if necessary), and click *Edit*.  Under the "IPv4  Settings" tab, set the *Method* to "Automatic (DHCP) addresses  only" and enter a third-party DNS server (e.g., Google's 8.8.8.8 ).

With any luck, this should solve your  problem.

---

