---
title: "Networking to a windows box"
date: 2005-09-16
forum: Desktop Environments
---

### Post by krajni on 2005-09-16
I am a first time linux user (unfortunately i have been using windows since 3.0) and i am loving Ubuntu, however before i formatted i backed up several gig of documents for my CCNA to an XP machine across the network in my frat house and am having trouble finding the computer on the network to retrieve my files.  Any suggestions?

---

### Post by KingBahamut on 2005-09-16
Making sure you have smbclient / smbfs installed. 

smbclient -L <ipaddressofthemachine>

if you have a valid share on the system........
then create a mount point somewhere , I typically create them in /mnt, something like /mnt/windows  -- 

mkdir /mnt/windows 

then do a 

mount -t smbfs -o username=<insertvalidusernamehere> //<ipaddressofmaching>/<sharename> /mnt/windows 

Itll ask for a password then, make sure you use an account that has access over the share your trying to use.

Once mounted 

cd /mnt/windows 

and then browse and move whatever you want or need.

---

### Post by rdick on 2005-09-16
I also am using Linus for the first time and are finding it very good to use. I am running a network where 3 Windows boxes are connected some wireless - some cabled. The Ububtu box is plugged directly to the router.

I can see the network and the files/folders but I would like to print from Linux using the WIn printers attached to the network. How can I do this? Some of our computer staff here are saying I should install Samba but since I can see the network is Samba installed already with the standard Ubuntu install. 

Any help would be appreciated. Thank you.

Randy

---

