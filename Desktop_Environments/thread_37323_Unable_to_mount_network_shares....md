---
title: "Unable to mount network shares..."
date: 2005-05-26
forum: Desktop Environments
---

### Post by Buelldozer on 2005-05-26
Hi,

I am completely unable to mount network shares using the mount command. I can't mount shares off my Win2K3 ADC or my RH FC3 box. Both of these shares worked until I formatted Suse 9.1 Pro off the box and put Warty on. It doesn't matter if I try and mount them as either SMBFS or CIFS, it always fails and it always fails with the maddeningly generic error of :

Mount: wrong fs type, bad option, bad superblock on //odin/users, missing codepage or other error.

A dmesg | tail reports the error:

smb_fill_super: missing data argument

On every mount attempt.

It doesn't matter whether I mount manually or through fstab, I get the same error.

Apt-get samba, samba-common, smblclient reports that I am using the most current version in all cases.

Here is the kicker, if I do an smbclient connection it works EVERY time.

What am I doing wrong?  :-?

---

### Post by Sleeper Service on 2005-05-26
Does it work if you try mounting the directories using 'nfs' rather than 'smbfs' or 'cifs'?

---

### Post by wilhelm on 2005-05-27
u might want to give the board the syntax of the command that you are using...
could be easier to help then :)

---

### Post by Sleeper Service on 2005-05-27
Sorry!

I've used:
[FONT=Courier New]mount -t nfs 192.168.0.2:/home/shared /mnt/shared[/FONT]

192.168.0.2:/home/shared has to be readable/writable/executable by anybody, and 192.168.0.2:/home/ has to be at least executable by anybody.

---

### Post by [pl]ice on 2005-05-31
i had the same, i think u're missing smbfs package ? ...

check if u can see the server first;  net share -I ip

any luck?

---

### Post by osde.info on 2005-06-01
have a look at [http://ubuntuforums.org/showpost.php?p=195128&postcount=14](http://ubuntuforums.org/showpost.php?p=195128&postcount=14)

---

### Post by monkman on 2005-06-16
```
 root@chateau-de-monk:/home/monkman # net share -I 192.168.0.3
Password:
E$
IPC$
D$
a
ADMIN$
C$
root@chateau-de-monk:/home/monkman #

```

so the network seems to work. but when i try to mount
```
root@chateau-de-monk:/home/monkman # mount -t smbfs //192.168.0.3/ /media/gego/
mount: wrong fs type, bad option, bad superblock on //192.168.0.3/,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

lsmod says smbfs module is loaded, so what can be left?

thanx for your help!

---

### Post by Rounan on 2005-06-18
I'm having the same problem.

Fresh Ubuntu install, followed ubuntuguide.org to add programs.

I recently installed ubuntu on 2 other boxes, and did not have problems on those...

I'm stumped.

---

### Post by monkman on 2005-06-19
it works using konqueror --> network folders --> samba shares --> workgoup --> etc          

strange enough that it doesn't work manually...

---

### Post by mrnegitoro on 2005-06-20
Hello there,

I'm having the same problem, my mp3s are on another box so I'd like to mount them through fstab. Seems like this is affecting quite a few people. Any solutions?

Thanks!

---

### Post by mrnegitoro on 2005-06-21
Hey guys,

The solution is:

**apt-get install smbfs**

(below) Taken from: [http://us1.samba.org/samba/ftp/Binary_Packages/Debian/samba3/dists/stable/main/binary-i386/Packages](http://us1.samba.org/samba/ftp/Binary_Packages/Debian/samba3/dists/stable/main/binary-i386/Packages) 

> 
Package: smbfs
Version: 3.0.14a-1
Priority: optional
Section: otherosfs
Maintainer: Simo Sorce <idra@samba.org>
Depends: netbase (>= 2.02), samba-common (= 3.0.14a-1), e2fsprogs (>= 1.27-2), libattr1, libc6 (>= 2.2.4-4), libcomerr2, libkrb53, libldap2 (>= 2.0.23-1)
Suggests: smbclient
Conflicts: smbfsx, suidmanager (<< 0.50)
Replaces: smbfsx
Architecture: i386
Filename: dists/stable/main/binary-i386/smbfs_3.0.14a-1_i386.deb
Size: 322846
MD5sum: b14003a2f338eebca60c74fd35f809ab
Description: mount and umount commands for the smbfs (for kernels >= than 2.2.x)
 Smbfs is a filesystem which understands the SMB protocol.
 This is the protocol Windows for Workgroups, Windows NT or
 LAN Manager use to talk to each other. It was inspired by
 samba, the program by Andrew Tridgell that turns any unix
 site into a file server for DOS or Windows clients.
 .
 If you want to use command-line utilities like smbclient, smbtar
 and/or smbspool you just need to install the smbclient package.
 .
 Starting with the Debian Samba packages version 2.2.0-1, the old smbfs
 utilities for 2.0.x have been removed. There are no wrapper scripts
 that call a specific smbmount/smbumount depending on the kernel
 version.  If you are using a 2.0.x kernel please upgrade or use the
 latest Samba 2.0.7 Debian package.
installed-size: 764
source: samba
 

Hope this helps!

---

### Post by Ranime on 2005-06-21
I had the same problems... all the errors, blablablah...

When I changed  the credentials to that of the **Administrator**-user, it just mounted without problems...

*Update:* 
I created a new user on my windows box. Gave it all the rights it needs and changed the contents of /root/smbcredentials (see [Ubuntu guide for mounting smb shares](http://www.ubuntuguide.org/#automountnetworkfoldersall)).

```
username=ubuntu(host)name
password=12345abc
```

Works like a charm now!  :grin:

---

### Post by monkman on 2005-06-24
apt-get install smbfs

helped me out, i didn't think it could because lsmod showed up smbfs  ;)

---

### Post by mindwarp on 2005-06-29
Same issue here, can't mount a samba share and get same error message. apt-get install smbfs fixed it, and I too didn't think that was the problem since I saw it in LS mod.

---

### Post by n0ah on 2005-12-22
[QUOTE=monkman]apt-get install smbfs

helped me out, i didn't think it could because lsmod showed up smbfs  ;)[/QUOTE]


i fuckin love you man.. i've been working on this for 3 days and couldn't figure it out for the life of me.. 

thank you thank you thank you!

---

### Post by Drakonis on 2006-01-25
Im having the same problem, ive tried everything suggested in this thread and nothing has worked. 

"apt-get install smbfs" results in:

Reading package lists... Done
Building dependency tree... Done
Package smbfs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package smbfs has no installation candidate

trying to mount ( sudo mount /mnt/seaquest ) results in:

mount: wrong fs type, bad option, bad superblock on //seaquest/shares,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

What am I missing here?  Ive tried changing the file system type to nfs when mounting but that doesnt work either.  Ive edited fstab, created the credentials file, but not having any luck.

---

### Post by Jason_25 on 2006-01-25
[QUOTE=Drakonis]Im having the same problem, ive tried everything suggested in this thread and nothing has worked. 

"apt-get install smbfs" results in:

Reading package lists... Done
Building dependency tree... Done
Package smbfs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package smbfs has no installation candidate

trying to mount ( sudo mount /mnt/seaquest ) results in:

mount: wrong fs type, bad option, bad superblock on //seaquest/shares,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

What am I missing here?  Ive tried changing the file system type to nfs when mounting but that doesnt work either.  Ive edited fstab, created the credentials file, but not having any luck.[/QUOTE]

I think you are missing the restricted or universe repos.  

In Synaptic choose repositories, then choose settings, and check 'show disabled software sources'.  Check all of them.  Once you close synaptic, run the apt-get command again.

---

### Post by Drakonis on 2006-01-25
[QUOTE=Jason_25]I think you are missing the restricted or universe repos.  

In Synaptic choose repositories, then choose settings, and check 'show disabled software sources'.  Check all of them.  Once you close synaptic, run the apt-get command again.[/QUOTE]


That did it, i got my shares mounted.  Thanks.

---

