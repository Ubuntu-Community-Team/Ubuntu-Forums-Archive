---
title: "desktop setup - homefolder on server"
date: 2011-01-17
forum: Desktop Environments
---

### Post by Niels_Andersen on 2011-01-17
Hello.
I'm new to this forum, but here goes my question.

I'm trying to migrate from win7 to Ubuntu. I have used a Turnkey fileserver for a while now, with the following setup:
4 hdd
hd1 /boot partition
      /swap partition
      /root partition
      /home partition (100gb)
      /lvm partition (200gb)
hd 2-3 and 4 /lvm

On my windows setup i have a separate server (win2003) running the entire family's separate Document folders, mounted to each user through a simple .bat and some registry changes. (that took me a while to figure out ;))


  Now I want to do basically the same and use the /home folder on the Turnkey fileserver for every user logging on to their respective pc’s (a couple of laptops and some stationary pc’s).
  

Is this possible? 



I’ve looked into nfs, following this guide: [https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS%20Client](https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS%20Client) and it seems to work, but I’m a little uncertain how to mount the home folder to the nfs server on the client.
  

I have tried to mount like this:
  Nfs on /mnt with this command: 

mount -t nfs4 -o proto=tcp,port=2049 nfs-server:/users  /mnt, 

I can see my “home” folder from the server in the /mnt folder, and have copied some files to be sure. but now when i edit /etc/fstab to mount at startup with this: 

nfs-server:/users   /mnt   nfs4    _netdev,auto  0  0,
I get mount errors at bootup.

  

If I use this command: 

mount -t nfs4 -o proto=tcp,port=2049 nfs-server:/users  /home, 

and edit /etc/fstab with: 

nfs-server:/users   /home   nfs4    _netdev,auto  0  0,
 I get the same errors. 
  

I think that there is no network, and the computer cant reach the nfs-server…?
  

Any other useful suggestions?
  

I’m still testing it on my Xenserver, but I just thought I would ask here before I go any further.
  And i'm really tired of my windows setup, and the money i'm throwing at Redmond, so ANY suggestion or solution would be appreciated.


Niels.

---

### Post by Lukiwuki on 2011-01-17
Has the NFSServer a static IP?
Then try using the static ip.
Example ( the nfs server has the IP 192.168.10.15
192.168.10.15:/users /home nfs4 _netdev,auto 0 0

Let me know the result.

---

### Post by Niels_Andersen on 2011-01-17
I changed it to static ip, and edited the /etc/fstab accordingly, and voila... 
Now i mounted with the:
mount -t nfs4 -o proto=tcp,port=2049 ip of server:/users  /home
that worked. no errors.
Now comes the next issue...
I have copied my entire home folder to the server, including hidden files, and time will tell if that is agood idea 8-[
Thank god, it's on a xenserver, so i can snapshot back. 

On second thought, that was not nessecary, since it is just pictures and other stuff thats on the windows server...
Still learning :p
I will post back on observations since this is a topic often brought up in the forum.

---

