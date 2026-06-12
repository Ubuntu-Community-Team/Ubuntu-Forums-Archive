---
title: "Mount ISOs without root permissiosn"
date: 2006-08-22
forum: Desktop Environments
---

### Post by Tortanick on 2006-08-22
Just wondering if there is any way to mount .ISO files without useing sudo.

---

### Post by amohanty on 2006-08-23
The only way to mount isos that I know of (in linux, i think the bsds do it differently) is:
**mount -t iso9660 -o loop x.iso mnt**
pmount allows you to mount things without being root, unfortunately pmount does not accept the -o option. So you are kind of stuck.

Of course, I cannot guarantee that there isnt any other way, just that I havent really seen any other way.

HTH
AM

---

### Post by Tortanick on 2006-08-23
Any idea if I can just chgrp/chmod the mount binary so it allows anyone with the mount group to use it?

---

### Post by amohanty on 2006-08-23
I think you can suid it, but its usually not advisable, because that poses a security risk. You can however:

1. write a shell script that explicitely mounts the iso only
2. put the script in /usr/local/bin
3. suid that script or od some fancy /etc/sudoers stuff to allow specific users sudo access to only that script.

HTH
AM

---

### Post by Tortanick on 2006-08-23
So its possible but above my level of skill.

---

### Post by amohanty on 2006-08-23
:) your skill level depends on how much time you are willing to spend on it. The more time you spend, the higher your skill level goes. :)

Another option is google, read up and then ask about things you couldnt figure out (it happens - more often than some ppl would like to admit).

Is there something in the previous post that you did not understand or dont know how to do?

AM

PS: 
Re:
>  UNIX: inventing better wheels since 1970
I would suggest a read of the excellent "Unix Haters Handbook" :) :
[http://www.simson.net/ref/ugh.pdf#search=%22the%20unix%20haters%20guide%22](http://www.simson.net/ref/ugh.pdf#search=%22the%20unix%20haters%20guide%22)
Gives 'All that glitters is not gold' a whole new meaning.

---

### Post by Tortanick on 2006-08-24
Well suid shellscripts don't work in linux, according to [this article]("http://www.samag.com/documents/s=1149/sam0106a/0106a.htm").

And if I have sudo permission for that script alone then its as vunerable as SUID shellscripts

That leaves me with mounting ISOs in perl (or maby python can have suid) but either way I don't know how to write a perl/python script that lets users mount iso files, only when they have read permissions for the iso and only when they have write permissions to the mount point. I may teach myself but it won't be fast

P.S. my sig is a response to everyone who complains about distros because "focusing on one will make a good distro" Dispite the fact most distros easily top MS and the obvious advantages of speciliseation, even if I agree that every now and again varous distros should step back and say, have we been beaten on this feature, and for example use alien to move from RPM to debs

Really it should say something about specialised wheels but I couldn't get a snappy enough phrase. I'll read that handbook

---

### Post by peabody on 2006-08-24
> **amohanty said:**
> I think you can suid it, but its usually not advisable, because that poses a security risk. You can however:


Mount IS suid. It's so that entries maked as "users" in the /etc/fstab can be mounted.

---

### Post by amohanty on 2006-08-25
> 
Mount IS suid. It's so that entries maked as "users" in the /etc/fstab can be mounted.

Usually yes. However in dapper (I am not 100% sure because I dont have access to my machine, so please correct me if I am wrong) the suid'ed command is **pmount **and not mount, so if you were to try using mount even for a dev listed in fstab as a normal user, you would be kicked out. Again I am not certain fo this, I will have to crosscheck on my boxen.

> Well suid shellscripts don't work in linux, according to this article.

Sorry about the suggestion, didnt know that, never really had to do that. How about mounting it via /etc/fstab then if this is a file system that is going to be around for quite a while.

AM

---

### Post by peabody on 2006-08-27
```

$ ls -l `which mount`

-rwsr-xr-x 1 root root 75088 2006-05-15 18:43 /bin/mount

```

Running dapper.

---

### Post by amohanty on 2006-09-05
> **peabody said:**
> ```

$ ls -l `which mount`

-rwsr-xr-x 1 root root 75088 2006-05-15 18:43 /bin/mount

```

Running dapper.

That is correct, however, based on my experience, only root can mount devices not listed in /etc/fstab with the user options. Last time I tried to find out the reason why (this was a lomg time back..) it had something to do with the fact that user mounts are a security issue and that /dev device files are not accessible to regular users so mount cannot really do anything. The ways around it were the sudoers list and user mounts in fstab. Unfortunately I am not guru enough to know _exactly_ why this is, but would love to find out. Google has not been very helpful of late. So if you do find out, let me know.

Thanks.
AM

---

