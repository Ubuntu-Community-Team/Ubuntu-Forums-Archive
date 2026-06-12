---
title: "Permissions problem"
date: 2013-06-16
forum: Desktop Environments
---

### Post by jmcgee on 2013-06-16
I have PVR1, acting as file server and mythbackend, with internal drive mounted at /mnt/media3
I also have acerrevo acting as mythfrontend.  I log onto each as user name mythuser. 

MythTv can't delete files, and I'm assuming this is because of permissions.

```
mythuser@PVR1:/mnt/media3/myth/recordings$ id mythuser
uid=1001(mythuser) gid=125(mythtv) groups=125(mythtv),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),44(video),46(plugdev),105(scanner),107(fuse),109(lpadmin),115(admin),121(netdev),127(sambashare)
```

```

mythuser@acerrevo:/mnt/media3$ id mythuser
uid=1001(mythuser) gid=1001(mythuser) groups=1001(mythuser),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),44(video),46(plugdev),104(fuse),112(netdev),119(admin),121(nopasswdlogin),122(sambashare),123(mythtv)
```

I brute forced the solution earlier with chmod 777, but I want to get it right.

My guess is the GID needs to match, and maybe UID?  

So on the client (acerrevo) to try and match the gid to the server, I did

```
mythuser@acerrevo:/mnt/media3$ groupmod --gid 125 123
groupmod: group '123' does not exist

```

what am I missing?

---

### Post by ShadowVegan on 2013-06-16
Right click on a file and see who the owner is and who can change content. Also try removing a file with sudo using the terminal
```
sudo rm <file path/file name>
```

---

### Post by Bashing-om on 2013-06-16
[COLOR=#000000]ShadowVegan; Hi !
As an observation, neither of your ends have "sudo" access. For reference, mine:
[/COLOR]> sysop@1304mini:~$ iduid=1000(sysop) gid=1000(sysop) groups=1000(sysop),4(adm),24(cdrom),27(sudo),29(audio),30(dip),46(plugdev),108(lpadmin),109(sambashare)
sysop@1304mini:~$ 
27(sudo); do you need to add that user to the sudo group ?
[INDENT=2]
just a thought

[/INDENT]

---

### Post by steeldriver on 2013-06-16
as well as needing to do the groupmod from a 'sudo' account, you will probably need to give the actual target group name (mythtv), rather than its *current* gid i.e.

```
sudo groupmod -gid 125 mythtv
```

e.g.

```

$ sudo groupadd --system mythtv
$ 
$ getent group mythtv
mythtv:x:999:
$
$ sudo groupmod -g 127 999
groupmod: group '999' does not exist
$
$ sudo groupmod -g 127 mythtv
$ getent group mythtv
mythtv:x:127:
$ 

```

Obviously the gid 125 needs to be available on the acerrevo machine (it wasn't on mine - which is why I used 127 above)

---

