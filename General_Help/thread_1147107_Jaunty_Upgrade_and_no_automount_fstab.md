---
title: "Jaunty Upgrade and no automount fstab"
date: 2009-05-03
forum: General Help
---

### Post by jame86 on 2009-05-03
Hi all,

I have done some searching and came up fruitless, so sorry if this has already been answered.

Following my upgrade to 9.04, on boot my fstab doesn't load correctly.  All local devices are present, but any remote drives (NFS) are unmounted.  Running "mount -a" solves the problem with no errors.

This is happening on two boxes, one Ubuntu and one Xubuntu.

Any advice would be great.

Thanks

Damingo

](*,)

---

### Post by Kai-vana on 2009-05-04
Im getting the same problem so...

BUMP.

---

### Post by kpkeerthi on 2009-05-04
Can you post the fstab contents?

---

### Post by canadiandude007 on 2009-05-04
Have you tried running the command:
> fdisk -l
To see what it returns?  Are you even seeing them listed?  What are the contents of your fstab file?

Do a > sudo cp /etc/fstab /etc/fstab_backup first and then we can see if we can get this working for you.

---

### Post by jame86 on 2009-05-07
Sorry for the late response!

Two machines:

Paladon:

10.10.10.201: /mnt/1tb/   /mnt/1tb   nfs   rw   0   0


Kaynine (the pc listed in paladons fstab)

UUID=f8ade4a7-6cc9-48e6-8dee-d09427aa090b   /mnt/1tb   ext3


Both of the above do not mount on boot.  But upon running "sudo mount -a" both mount fine, without any errors.

Thanks

---

### Post by rinishak on 2009-05-09
Hi there,

I'm having the same problem here. After entering the lines to automount my two Windows partitions in the fstab, when I login, they aren't mounted. When I try to access the partitions via the GNOME Places menu, I get a message that goes along the lines of "You do not have the privileges to mount this partition."

However, as jame86 has mentioned, I can mount it without errors by typing:

```
sudo mount -a
```

in the terminal. How can I acquire these privileges at startup?

Thanks in advance,
Rin

---

### Post by punknroll on 2009-05-18
same problem here. here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=c3fc3b0a-f524-43c0-98cf-8b1fcc3dd94b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=3ac857c0-d88b-423f-a31f-89082a0d96ed none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
//ubuntu/lampp_htdocs  /media/develop  cifs      credentials=/etc/samba/user,uid=myuser,gid=myuser,noexec,nounix  0 0
//ubuntu/my_space  /media/sf_space  cifs      credentials=/etc/samba/user,uid=myuser,gid=myuser,noexec,nounix  0 0
//server/daten$         /media/win2003  cifs uid=myuser,gid=myuser,iocharset=utf8,credentials=/etc/samba/userwin2003,domain=MYDOMAIN,umask=0022,nounix,noexec         0       0

---

### Post by jame86 on 2009-06-13
sorry to BUMP so late after i first posted.

but did anyone find a solution

---

### Post by PureLoneWolf on 2009-06-13
I had this exact issue - I overcame it by editing /etc/rc.local and specifying mount -a above the exit 0 line

Works perfectly for me

---

### Post by jame86 on 2009-06-14
Thanks for that, it worked great on one machine. but strangely not on the other!!

D

---

### Post by jame86 on 2009-12-12
As a tidy up,  the problem was solved as soon as I updated to 9.10.  Never did find what caused it though!!

:(  :popcorn:

---

