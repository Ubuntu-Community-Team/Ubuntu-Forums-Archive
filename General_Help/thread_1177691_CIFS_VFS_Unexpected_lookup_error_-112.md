---
title: "CIFS VFS: Unexpected lookup error -112"
date: 2009-06-03
forum: General Help
---

### Post by trinaryouroboros on 2009-06-03
I'm having some trouble locating information on this, I'm using Ubuntu Intrepid Ibex 64-bit - output of dmesg | tail:

[84887.404143]  CIFS VFS: Unexpected lookup error -112
[84897.404033]  CIFS VFS: Unexpected lookup error -112
[84907.404031]  CIFS VFS: Unexpected lookup error -112
[84917.405184]  CIFS VFS: Unexpected lookup error -112
[84927.404031]  CIFS VFS: Unexpected lookup error -112
[84937.408018]  CIFS VFS: Unexpected lookup error -112
[84947.408034]  CIFS VFS: Unexpected lookup error -112
[84957.408026]  CIFS VFS: Unexpected lookup error -112
[84967.408623]  CIFS VFS: Unexpected lookup error -112
[164688.891345]  CIFS VFS: No response for cmd 50 mid 41834

If you'll ask me, is this affecting something...I'm going to have to say...no...I don't think so?

:?

---

### Post by DragonAX on 2009-06-19
Could be some unreachable network shares?
I had these errors on startup and attempting to suspend. So I commented out all the network mounts in /etc/fstab and for some reason I also had one in /etc/mtab. Seems to have fixed it but I have only tested suspend and restart a couple of times so I guess time will tell...

---

### Post by tulli0 on 2010-02-17
I have the same problem, i work all day for resolv it, i try with different options in /etc/fstab and i find a compromise, a line in my fstab is:
" //192.168.200.3/DatiUte /rete/DatiUte cifs username=utente,password=xxxxxx,rw,uid=utente,gui=utente 0 0 " 
i remove the ",gui=utente"  and the problem go out, i try this with two pc and the result are the same, now i work fine and i can read, write and move into a cifs dirtectory with no problem.

---

### Post by trinaryouroboros on 2010-02-23
> **tulli0 said:**
> I have the same problem, i work all day for resolv it, i try with different options in /etc/fstab and i find a compromise, a line in my fstab is:
" //192.168.200.3/DatiUte /rete/DatiUte cifs username=utente,password=xxxxxx,rw,uid=utente,gui=utente 0 0 " 
i remove the ",gui=utente"  and the problem go out, i try this with two pc and the result are the same, now i work fine and i can read, write and move into a cifs dirtectory with no problem.

I've upgraded to 9.10 and haven't had a problem since, however, I may have corrected the issue myself at some point in time, this was a while ago...

Your issue with the mount line is potentially a uid/gid problem?  I'm not sure, but for my example, I use the actual ID number, so it would look more like:

uid=500,gid=500

I don't know what "gui=" is for...never used it, maybe that's a typo?

You can find your UID/GID numbers in /etc/group, by the way. Let us know if this helps.

I do recall, at some point in time that I had to actually put in GID/UID of my actual User, in order to get this working smoothly in ubuntu since ibex.

---

### Post by erik.lonroth on 2010-09-09
I use 10.04 x86_64

I use automount /home/<username>

cat auto.master
```
/home auto.samba --timeout=60
```

cat auto.samba
```
* -fstype=smbfs,guest ://smbserver01/homes/&
```

(Samba shares does not need a login, guest account = )


Samba settings from /etc/samba/smb.conf

```

usershare allow guests = yes

[homes]
   comment = Raided homes
   path = /srv/export/homes
   read only = no 
   public = yes
```

Everything works good for all users, but the

```
Re: CIFS VFS: Unexpected lookup error -112
```

Is occuring sometimes after idle time on computer. Probably some timeout/disconnect thing or a mount issue... dunno.

---

### Post by trinaryouroboros on 2010-09-16
> **erik.lonroth said:**
> I use 10.04 x86_64

I use automount /home/<username>

cat auto.master
```
/home auto.samba --timeout=60
```

cat auto.samba
```
* -fstype=smbfs,guest ://smbserver01/homes/&
```

(Samba shares does not need a login, guest account = )


Samba settings from /etc/samba/smb.conf

```

usershare allow guests = yes

[homes]
   comment = Raided homes
   path = /srv/export/homes
   read only = no 
   public = yes
```

Everything works good for all users, but the

```
Re: CIFS VFS: Unexpected lookup error -112
```

Is occuring sometimes after idle time on computer. Probably some timeout/disconnect thing or a mount issue... dunno.


No clue, this stuff is still happening on my 10.04 using samba, also on servers, x64.  It doesn't seem to affect anything but logging, AFAIK

---

### Post by andrewjessop on 2013-02-18
This is happening for me as well.  I'm running Ubuntu 12.04.1 LTS, kernel: 3.2.0-37-generic x86_64.

I have a single CIFS mount:
//shared.domain/shared on /shared type cifs (rw,nosuid,nodev)

When this error occurs it locks up all of Cinnamon, will not allow creation of new process(s) or termination of existing ones until the error resolves itself.  It is very annoying because it renders the whole computer useless for an indeterminate amount of time.

From a quick grep of the kernel source, this message comes from the cifs.ko kernel module - specifically from the cifs_lookup() function in dir.c.  I don't know what the return code of -112 means though.

Edit: Looking at the file /usr/include/asm-generic/errno.h
Return code 112 is EHOSTDOWN.  So it appears that the box the share I'm mounting is on keeps rebooting.  I'm a little confused about why this brings my system to its knees though.

---

### Post by wildmanne39 on 2013-02-18
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

