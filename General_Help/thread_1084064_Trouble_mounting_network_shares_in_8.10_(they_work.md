---
title: "Trouble mounting network shares in 8.10 (they worked in 7.10!)"
date: 2009-03-01
forum: General Help
---

### Post by dphirschler on 2009-03-01
My Ubuntu box upstairs (Ubuntu 7.10) automatically mounts my network shares via fstab.  When I built a second Ubuntu box downstairs (this time using Ubuntu 8.10), I copied those lines from fstab, and well... it doesn't work.  So my question is, why?  Did something change in version 8.10?  And how do I get the drives to connect?


Darryl

---

### Post by dphirschler on 2009-03-02
FWIW, here are the lines from fstab.  This works on the 7.10 PC upstairs but not the 8.10 PC downstairs.

```
/dev/sdb1	/home/darryl/Videos	ext3	defaults	0	2
//192.168.1.99/C/video	/mnt/thurgood	cifs	defaults	0	0
//server1/share 	/mnt/server1	smb	username="xxxxxx",password="xxxxxxxxx"	0	0

```

//192.168.1.99 (aka 'Thurgood') is a Windows XP machine.  //server1 is an Ubuntu (8.10) machine I set up as a file server.  Of course I blocked out my username and password for this post.


Darryl

---

### Post by geirha on 2009-03-02
Open a terminal and run ```
sudo mount -a
``` That command will attempt to mount all entries in fstab that aren't currently mounted and that does not have the noauto option. If it fails to mount some filesystems, it should print a message explaining why. Hopefully it will be a useful messages.

---

### Post by dphirschler on 2009-03-02
It prompted for a password and then gave the following message.

mount: unknown filesystem type 'smb'

I checked both shares and thurgood mounted, but not server1.  I don't know what changed about thurgood except that it is now plugged into the network instead of wireless.  Oh, wait a minute... the static IP will not work if connected via wireless will it?  Time for some tests.

In the meantime, what about server1?  Why is it failing?


Darryl

---

### Post by geirha on 2009-03-02
The proper name should be smbfs, but cifs is the newer type, so better change it to cifs.

Oh, and, it is likely that the fstab entries are mounted before the wireless is connected ... If that is the case, then you might have to add a script to run when the network interface is connected. Look in /etc/network/if-up.d/. Copy one of those scripts and change it to run "mount /mnt/thurgood" etc. when the interface is connected.

---

### Post by dphirschler on 2009-03-02
OK, i changed 'smb' to 'cifs' and now I get this:

```
mount error: could not find target server. TCP name server1/share not found
No ip address specified and hostname not found
```

Looks like it is expecting an ip address.  But I did not need one to mount the drives on the Ubuntu Gutsy (7.10) box.

Oh, and I was probably not clear about the wireless.  It's my Windows laptop that was wireless.  This Ubuntu machine (and currently the laptop) is wired in.  I suspect my earlier troubles with mounting the laptop's share was because the laptop at the time was wirelessly connected to the network, and so the IP was most likely assigned by the router instead of being 192.168.1.99 as stated in the fstab file.  Of course I haven't confirmed that yet.  It's only a theory.

But I cannot figure out why the server is not mounting.  I have no trouble navigating to it through the 'Places' menu.  I should be able to mount it through fstab.


Darryl

---

### Post by geirha on 2009-03-02
I'm not sure how the wins naming thing is done, so I'd go with dns. You'll want to add a mapping of ip-adress to host-name in /etc/hosts.

---

### Post by dphirschler on 2009-03-02
Is it as simple as adding the following to /etc/hosts?

```
192.168.1.98	server1
```


Darryl

---

### Post by geirha on 2009-03-03
Yep, that should do it.

---

### Post by dphirschler on 2009-03-03
That did it.  Thanks.  Any idea why this step was not necessary on the 7.10 machine?  Could it be because that machine has full-fledged Samba installed where this 8.10 machine only has smbfs installed?


Darryl

---

### Post by geirha on 2009-03-03
Yes, that's a possibility. When you have the full-fledged samba installed, it runs a couple of daemons, one of which probably handles those wins/netbios names. I don't have any windows machines, so I have no need for samba, and thus I don't know that much about it. ssh and sshfs does the trick for me.

---

