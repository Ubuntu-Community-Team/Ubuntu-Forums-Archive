---
title: "NFS Network Automount at book"
date: 2006-07-17
forum: Desktop Environments
---

### Post by Fitzsimmons on 2006-07-17
Hey, I've got the following NFS lines in my fstab:

mothership:/usr/home/justin/masters /home/justin/masters        nfs     defaults,sync,rsize=32768,wsize=32768 0 0
mothership:/usr/home/justin/lossy /home/justin/lossy            nfs     defaults,sync,rsize=32768,wsize=32768 0 0

These aren't being mounted at boot.  The lines themselves work, because I can issue (for example) sudo mount /home/justin/masters to mount the share, or just issue a sudo mount -a to pick them up as well.

I suspect the reason why it isn't working is because the fstab is scanned before network support is up.  Is there a prepackaged init script that requires networking to be up that will mount network shares during the boot, or do I have to write my own?

---

### Post by tturrisi on 2006-07-17
[http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by Fitzsimmons on 2006-07-17
Thanks for nothing, *******.  Maybe you could try reading my post before kneejerking a response to an unrelated FAQ.

---

### Post by skirkpatrick on 2006-07-17
I have the same problem with Samba mounts.  Always have.

---

### Post by LichiMan on 2006-07-27
I have the same problem too, with samba.

---

### Post by tomski on 2006-08-04
Tried that but i get:
```

mount: wrong fs type, bad option, bad superblock on //192.168.1.1/public,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
i did have it running perfectly with this in fstab:
```

192.168.1.1:/public  /media/Fwall  nfs  user,suid,dev,exec  0  0

```
but since i have accessed this network in my local install of winXP it does not want to work all most as if Samba is overiding NFS??

I would rather access this share via NFS under linux, because then i can execute/play the files rather than copy them!

Any thoughts??

---

### Post by gilbert_george on 2006-09-05
Hi,

I have an ubuntu server and laptop (which uses wifi) and have had the same problems you describe with automounting nfs shares on the server onto the laptop.

It works fine if I mount them manually once the laptop is booted but totally (or interestingly sometimes partially - some shares mount some don't) when is automounts at boot.

This all used to work perfectly when both server and laptop were running breezy, but has been broken ever since I upgraded both to dapper.

Hope someone has a solution to this.

PS pls no links to NTSHowTo's or the like unless they specifically cover this issue.

---

### Post by Jaxonpants on 2006-11-23
I followed instructions in the Dapper manual to get nfs working between my desktop and my local server.

The line in fstab I ended up with was

hermes:/media/hdb1 /media/hermes        nfs     auto,rsize=8192,timeo=14,intr

And when I wanted to add a different share, I added another line:

hermes:/var/www /home/jackson/www       nfs     auto,rsize=8192,timeo=14,intr

The odd thing is, the /media/hermes mounts automatically, while /home/jackson/www doesn't.  ANd I just thought of this this second, but would /home being a seperate drive from / make any difference?

---

### Post by marc_c on 2006-11-24
I was having the same problem (nfs shares wouldn't mount at boot) and after I read your last post, decided it might have something to do with position in fstab file.  Moved the nfs mount entry farther up to where it wasn't last fstab entry and rebooted and the shares mounted at boot.  Worth a shot.

---

### Post by autosuggested on 2006-11-30
Hi there,

I had much the same problem in Dapper where my nfs shares never mounted at boot and I reported a bug which was marked as a duplicate of this one: [https://launchpad.net/distros/ubuntu/+source/sysvinit/+bug/46516](https://launchpad.net/distros/ubuntu/+source/sysvinit/+bug/46516)

Since I moved to Edgy my nfs entries in /etc/fstab seem to mount around 50% of the time.

---

### Post by fnjordy on 2007-02-02
I would add the NFS server hostnames to /etc/hosts and you can add "_netdev" to the options for each line in fstab.

Just had the same problem :KS

---

### Post by colossus73 on 2007-07-09
Hi,

does anyone know how to have the icons of the automounted NFS folders on the desktop? I'm using Xubuntu.

Thanks,

---

