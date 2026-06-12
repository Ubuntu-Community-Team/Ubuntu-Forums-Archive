---
title: "XP shared folder not showing up in Ubuntu"
date: 2011-08-20
forum: Desktop Environments
---

### Post by Heeter on 2011-08-20
Hi All,

Would like to see a couple of shared folders from an XP machine on my Ubuntu desktop. I am checking in the Network ->Windows Network folders.

What do I need to do to Ubuntu to make them show up?

Thanks

Heeter

---

### Post by darkdragn on 2011-08-20
For any number of reasons they might not want to show up... and it could take a while to explore all of the possibilities. As an alternative you could mount it manually. If you don't know the name of the share, but you know the IP then you can get a list of all shares with the following command(Replace $RemoteIP with the actual IP):
 
```
 
smbclient -L $RemoteIP

```
If there are no results from that command then either you can't reach that IP or it's not really sharing the folders. If there are results then you can manually mount, if you'd like. The following is an example of that:
 
```
 
mkdir /mnt/windowsShare
mount -t cifs -o username=darkdragn //$RemoteIP/$shareName /mnt/windowsShare
 

```I only did the mkdir so we had somewhere to mount it. If you have the smbfs package installed than this will prompt you for a password, if not then you may have to put ',password=' after the username on the -o argument. Aside from that just make sure you change $RemoteIP with the actual IP and $shareName with the actual name of the share.
 
Oh, I also forgot. If the share is accepting guest connections, you can omit the username portion, and just use guest. For example:
```
 
mount -t cifs -o guest //$RemoteIP/$shareName /mnt/windowsShare
```

---

### Post by Heeter on 2011-08-21
Hey, 

Thanks Darkdragon.

Worked like a charm.....

Thanks again,

Heeter

---

