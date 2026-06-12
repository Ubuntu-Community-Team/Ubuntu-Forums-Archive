---
title: "CIFS not mounting at startup"
date: 2009-04-22
forum: General Help
---

### Post by danduq on 2009-04-22
Hi,

Since upgrading to Intrepid I have been using CIFS instead of SMBFS to mount my Samba shares in fstab. However, recently I broke my network settings and ended up installing wicd (which has sorted everything and is brilliant), since then my CIFS shares aren't mounting at startup, although running a "sudo mount -a" afterwards works fine.

Here is an example entry from my fstab;
```
//server/share	/mnt/server/share	cifs    credentials=/root/.credentials,nounix,nodfs,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

The server is specified in my /etc/hosts file, and is on the same network as me, so shouldn't be timing out finding the host.

I can't find any (obviously) related errors in syslog or messages.

Any help gratefully received!

---

### Post by MrWES on 2009-04-22
> **danduq said:**
> Hi,

Since upgrading to Intrepid I have been using CIFS instead of SMBFS to mount my Samba shares in fstab. However, recently I broke my network settings and ended up installing wicd (which has sorted everything and is brilliant), since then my CIFS shares aren't mounting at startup, although running a "sudo mount -a" afterwards works fine.

Here is an example entry from my fstab;
```
//server/share	/mnt/server/share	cifs    credentials=/root/.credentials,nounix,nodfs,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

The server is specified in my /etc/hosts file, and is on the same network as me, so shouldn't be timing out finding the host.

I can't find any (obviously) related errors in syslog or messages.

Any help gratefully received!

You named your server, server in your /etc/hosts ? Also you might want to add _nodev to your fstab entry. Dmesg will balk at it, but it prevents mounting of the cifs shares until a network connection is present. Also, no other error messages in dmesg?


Bill

---

### Post by danduq on 2009-04-22
> **MrWES said:**
> You named your server, server in your /etc/hosts ? Also you might want to add _nodev to your fstab entry. Dmesg will balk at it, but it prevents mounting of the cifs shares until a network connection is present. Also, no other error messages in dmesg?


Hi Bill,

No, "server" was just an example, perhaps a bad one!  ;)

Can't find anything in /var/log/dmesg, no.

---

### Post by MrWES on 2009-04-22
Did you add the _nodev to the fstab line?

Shoot -- actually it's _netdev

The option _netdev is always recommended for cifs mounts in fstab. Option _netdev delays mounting until the network has been enabled.

Sorry about the confusion.

Bill

---

### Post by danduq on 2009-04-22
I added _netdev and when doing a "sudo mount -a" I got this in my syslog;
 CIFS: Unknown mount option _netdev
Although it did mount the drives.

When I rebooted though it didn't mount them again. The only entries I can find in syslog that mention "mount", "cifs" or "netdev" are
 Mount-cache hash table entries: 512
 EXT3-fs: mounted filesystem with ordered data mode.

And in dmesg;
 ADDRCONF(NETDEV_UP): eth0: link is not ready
 ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

Did I add it to the right place in my fstab?
```
//servername/share		/mnt/servername/admin	cifs    _netdev,credentials=/root/.credentials,nounix,nodfs,iocharset=utf8,file_mode=0777,dir_mode=0777, 0 0
```

---

### Post by MrWES on 2009-04-22
> **danduq said:**
> I added _netdev and when doing a "sudo mount -a" I got this in my syslog;
 CIFS: Unknown mount option _netdev
Although it did mount the drives.

When I rebooted though it didn't mount them again. The only entries I can find in syslog that mention "mount", "cifs" or "netdev" are
 Mount-cache hash table entries: 512
 EXT3-fs: mounted filesystem with ordered data mode.

And in dmesg;
 ADDRCONF(NETDEV_UP): eth0: link is not ready
 ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

Did I add it to the right place in my fstab?
```
//servername/share		/mnt/servername/admin	cifs    _netdev,credentials=/root/.credentials,nounix,nodfs,iocharset=utf8,file_mode=0777,dir_mode=0777, 0 0
```

Yah like I said dmesg will balk at it. Here's my cifs mount from fstab
```
//192.168.1.101/MyFiles /home/bill/SharedFiles cifs credentials=/home/bill/.creds,_netdev,uid=bill,gid=users 0 0

```

---

### Post by danduq on 2009-04-23
I've added _netdev just after my credentials, I've corrected the "," I had on the end of my options and I've removed several of the options in order to try and eliminate them, so now my fstab entries take this form;

```
//servername/share        /mnt/servername/share     cifs    credentials=/root/.credentials,_netdev,nounix,iocharset=utf8,uid=dan,gid=company 0 0

```

The numeric GID of the group "company" is the same on both my laptop, the server I'm trying to mount and our LDAP server.

As I say, "sudo mount -a" successfully mounts the shares, although I do get the "CIFS: Unknown mount option _netdev" message in my syslog.

I still can't figure out why these aren't mounting at startup!  :confused:

---

### Post by imdano on 2009-04-23
I'm not sure why the share isn't mounting (my guess is it's related to you using wicd instead of NM), but as a workaround you can try adding the mount command as a post-connection script in wicd.

---

### Post by danduq on 2009-04-24
This is odd. I removed wicd (and I don't have Network Manager) so I'm running on manual IP config.

Now I get all my CIFS shares mounted at started. Hooray!
Except some of them are mounted twice! Booooo...

All the shares are on the same machine and using the same mount options.

---

### Post by Peter09 on 2009-04-24
If you are not using a wireless network you do not need network manager or wicd. Guess that may be something to do with it.

---

### Post by danduq on 2009-04-24
> **Peter09 said:**
> If you are not using a wireless network you do not need network manager or wicd. Guess that may be something to do with it.

Yeah. I initially installed Network Manager because I need to connect to a Cisco VPN occasionally, but it caused me so many problems with DNS and search domains that I had to remove it in order to see half the machines on my own network (this was when not connected to the VPN).

Seems that networking is a bit hit and miss. I can never quite get everything I want!  :)

Oh well, I guess having my drives mounted twice is better than not at all.

---

### Post by Peter09 on 2009-04-24
What happens if you cooment out the drive mount command from fstab, do they still mount (from whatever the second source is?)

---

### Post by danduq on 2009-04-28
> **Peter09 said:**
> What happens if you cooment out the drive mount command from fstab, do they still mount (from whatever the second source is?)

When I commented them out of fstab, they weren't mounted at startup, but when I un-commented them again, they were mounted twice.

Anyway, over the weekend I completely wiped my laptop and stuck a clean Jaunty installation on it. Now I have Network Manager successfully controlling my network with all the correct search domains and name servers and my CIFS mounts are mounted properly at startup.

I think I had probably fiddled around so much with the network settings over the last year that something was fundamentally wrong somewhere.

All OK now though!  :)  Thanks for all your help and suggestions.

---

