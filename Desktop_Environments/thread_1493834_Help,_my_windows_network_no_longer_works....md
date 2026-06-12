---
title: "Help, my windows network no longer works..."
date: 2010-05-26
forum: Desktop Environments
---

### Post by Jay2001 on 2010-05-26
If I go to...

Places > Network > Windows Network > MyActiveDirectoryDomain

I get the error...

Unable to mount location
Failed to retrieve share list from server
OK

This worked fine when Ubuntu was first installed but no longer does. It was a clean install of 10.04

I can still access shares on the domain by using fstab or the mount command to mount them directly but browsing fails.

Any one know what package I may have messed up?

---

### Post by Jay2001 on 2010-05-26
Sorry, this should be in the Networking forum, can it be moved?

---

### Post by 3rdalbum on 2010-05-26
Have you installed a personal firewall on the **client** computer? This can stop network browsing from working.

---

### Post by Jay2001 on 2010-05-26
No, no firewall. And to make things more complicated it seems I can browse to windows computers in a work group but not the domain, however I notice I am never getting password requests, not for domain or work group computers, could this be part of the problem?

---

### Post by Jay2001 on 2010-05-26
I have a feeling my smb.conf has been messed up, is there an easy way to reset it to it's default out of the box settings?

---

### Post by Jay2001 on 2010-05-26
If it helps, I just took the following screenshot when trying to browse the network with Smb4K.

---

### Post by QIII on 2010-05-26
Have you recently updated/upgraded?

Could you post the contents of /etc/hosts?

(Please redact any personal information with "X"s or whatever)

---

### Post by Jay2001 on 2010-05-26
no recent upgrades, was a fresh install at 10.04, all update applied however.

--------- /etc/hosts ------------

127.0.0.1 localhost
127.0.1.1 james-desktop.xxxxxxxxxxxxx james-desktop
# The following lines are desirable for IPv6 capable hosts
::1 localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---------------------------------

I did try installing Likewise Open to authenticate to the domain but gave it up as a bad job and removed it, could that have messed with my config?

---

### Post by Nythain on 2010-05-26
cant really help you much, but i had/have this problem too, so if you find a solution, make sure you post it... rather annoying problem when you keep trying to tell your friends that linux is the better between it and windows when dealing with networking

---

### Post by caliburn on 2010-05-26
I had a similar problem, a networked hard drive that I had previously been able to access via Samba suddenly became inaccessible - I could see it on Places-Network, but when I tried to access it I got [B]Failed to retrieve share list from server.
[/B]
The problem for me was that I had the networked drive defined in /etc/hosts with a fixed IP address e.g. 123.11.66.67 - however, the drive had been switched on and off  and had acquired a new IP address on the network - 123.11.66.68! It was only when I went to another PC which was working with the drive, and looked up IP address, that I realised the cause.

I changed /etc/hosts to reflect the correct IP and it works again.

Hope this might help...

---

### Post by QIII on 2010-05-26
I don't have much time, since the test I was running is about done and  I'll have to look at the results.
 
 I have had similar results in two situations:
 
 1.  My hosts file was changed (and yours looks a little bare, by the  way).
 
 2.  I shut down and recycled my router and lost the fixed assignment of  IP addresses to the individual machines.

I don't have any experience with Active Directory (software guy here, not a network guy), so this may be worth exactly doo-doo, but: 
 
 If you have a router, I would assign fixed IPs as appropriate, then  include them in your hosts file.

---

### Post by Jay2001 on 2010-05-27
I am still pretty sure my smb.conf file has got messed up, would doing a complete removal and reinstall of the smbclient package replace it or do I need to remove a lot more than that to get rid of the conf file?

---

### Post by Jay2001 on 2010-05-27
> **QIII said:**
> 1.  My hosts file was changed (and yours looks a little bare, by the  way).

Ideally a hosts file is pretty empty, that is what DNS is for surely, otherwise every time an IP changes you have to manually update the hosts file on every machine on your network.

> **QIII said:**
> 2.  I shut down and recycled my router and lost the fixed assignment of  IP addresses to the individual machines.

I don't have any experience with Active Directory (software guy here, not a network guy), so this may be worth exactly doo-doo, but: 
 
If you have a router, I would assign fixed IPs as appropriate, then  include them in your hosts file.

I actually run a DHCP server on one of our servers but I will try putting one or two machines into the hosts file, will let you know.

---

### Post by Jay2001 on 2010-05-27
ok, I added

# TEMP
192.168.0.41 server-db-01.xxxxxxxxxx server-db-01
192.168.0.39 server-mon-01.xxxxxxxxxx server-mon-01

to the bottom of my hosts file, still no joy.

Any other ideas?

---

### Post by QIII on 2010-05-27
Did you put that above the

"# The following lines are desirable for IPv6 capable hosts"

comment line?

---

### Post by stig on 2010-05-27
Since yesterday my network has been inaccessible and I'm getting exactly the same as Jay2001. I suspect it is due to one of the Ubuntu updates loaded in the last few days because nothing else has been changed on the PCs.

My /etc/hosts file is the same as Jay2001's except for the computer name of course. I'm not a computer expert, I just use 4 PCs to run my small home publishing business and learn whatever is necessary about Ubuntu as I go along. All the PCs are on 8.04 LTS and the network has been running perfectly for years. I set it up using the method described in Stormbringer's guide on these forums:
[http://ubuntuforums.org/showthread.php?t=202605&highlight=network+windows]("http://ubuntuforums.org/showthread.php?t=202605&highlight=network+windows")

My most recent updates are:
Commit Log for Wed May 26 11:15:40 2010
Upgraded the following packages:
libc6 (2.7-10ubuntu5) to 2.7-10ubuntu6
libc6-i686 (2.7-10ubuntu5) to 2.7-10ubuntu6

Commit Log for Mon May 24 11:11:39 2010
Installed the following packages:
gftp-common (2.0.18-17ubuntu1)
gftp-gtk (2.0.18-17ubuntu1)

I'm not sure whether the problem started before or after yesterday's libc6 updates, but it was definite after the gftp updates. I don't know enough about software to know if either of these updates would have any relevance to my network.

---

### Post by Jay2001 on 2010-05-28
> **QIII said:**
> Did you put that above the

"# The following lines are desirable for IPv6 capable hosts"

comment line?

I tried it in 3 different places in the file, top, middle and bottom, and as expected it made no difference.

I still think the hosts file is barking up the wrong tree, mostly for the following reason... My hosts file has not changed since the install, it never had any computers (other than mine) listed in it, and network browsing used to work.

---

### Post by Jay2001 on 2010-05-28
OK, I have good news and bad news.

Good) I have fixed the problem and can browse the network again.
Bad) I did it by replacing the smb.conf with one from a fresh install and as I suspected it all came back to life, unfortunately this doesn't help anyone else with the same issue who doesn't have a spare smb.conf hanging around.

Thanks for trying everyone.

---

### Post by stig on 2010-05-29
Jay2001's solution has worked for me, at least on one computer. There was a backup of the smb.conf from May 21st so I renamed the backup as the smb.conf and made the problem file smb.conf.old and now that PC accesses the network as before. On the other PC that I tried there was no backup but I pasted in the same text from the other backup and changed the username and computer name. It hasn't worked for this PC and I will next try starting with a default smb.conf and customising the settings. Can't do it just now because it's in use.

It seems odd that the files should suddenly stop working and it still worries me that an Ubuntu backup might have affected them in some way.

Thanks Jay2001 for relating your solution here.

---

### Post by stig on 2010-05-29
Well, it didn't work on the second computer. And after shutting down the first one for lunch and then restarting it, the network again doesn't work on that one either.

I've tried rebooting the router and I don't run a separate firewall on the PCs which might interfere so I'm at a loss to know why my network should suddenly die.

---

### Post by stig on 2010-06-01
After unsuccessfully trying other things, I un-installed Samba and then re-installed it on all my PCs. Now the network is functioning again. I still think the problem was caused by an Ubuntu update. If the problem had occurred on one computer only then it could be put down to a corrupt samba file but not when it occurred simultaneously on all my PCs.

---

