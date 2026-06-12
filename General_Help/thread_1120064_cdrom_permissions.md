---
title: "cdrom permissions"
date: 2009-04-08
forum: General Help
---

### Post by dokdoom on 2009-04-08
Somewhere down the road I screwed up the permissions on my cd/dvd drive and now when I insert a disc of any sort nothing shows up at all. The /media folder is set for my user. 

My question is, which files can I check to see the permissions that would allow my user to have access to the cd/dvd drive? 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=59c82e23-e110-42f9-a84a-a1f23effe555 /               ext3    relatime,errors=remount-ro 0       1
# /dev/mapper/vg-home
UUID=6a0fdcbd-11a7-43a9-be4f-d7521dc799e3 /home           xfs     relatime        0       2
# /dev/mapper/vg-tmp
UUID=0dd6ff4e-303a-4777-b238-ee7db3cf44f3 /tmp            xfs     relatime        0       2
# /dev/mapper/vg-usr
UUID=953a2b55-724e-4c83-9b90-f69d169bc6c8 /usr            xfs     relatime        0       2
# /dev/mapper/vg-var
UUID=942df03d-327c-48f6-b160-8a621bd221eb /var            xfs     relatime        0       2
# /dev/mapper/vg-swap
UUID=70fdc6af-b4c4-46f8-b46a-c0f08c44e081 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```


Thanks

---

### Post by dokdoom on 2009-04-08
Maybe I need to reword this, when I insert a cd. I don't get an icon on my desktop. And I can't find the cd in either cdrom file. So what would cause this to happen? Any thoughts?

---

### Post by oldos2er on 2009-04-08
In Gnome, click Places, and see if there's a menu entry named 'CD / DVD Drive' (or something similar). Are you able to access the CD from there?

 To check user permissions, click System, Administration, Users & Groups, Properties, User Privileges, and make sure 'Use CD-ROM drives' is checked.

---

### Post by dokdoom on 2009-04-08
> **oldos2er said:**
> In Gnome, click Places, and see if there's a menu entry named 'CD / DVD Drive' (or something similar). Are you able to access the CD from there?

 To check user permissions, click System, Administration, Users & Groups, Properties, User Privileges, and make sure 'Use CD-ROM drives' is checked.

I'm using xfce, but when I browse the GUI I can't see the cd in /media/cdrom or /media/cdrom.

I checked the User Privileges and 'Use CD-ROM drives' is checked. Thanks for your help with this, I am not having any luck on my own.

---

### Post by dokdoom on 2009-04-08
ls -al /dev/scd0 | awk '{print $3}'

This says the owner is root. Should it be my user by default?

---

### Post by dokdoom on 2009-04-08
I just inserted a 7.04 live cd and it loaded right up with

Failed to mount "Ubuntu 7.04 i386".
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: /dev/scd0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0.

I'm still able to see the files in /media/cdrom0 and it does show in Places (Which I didn't see earlier :/ )

---

### Post by dokdoom on 2009-04-08
I'm thinking of unmounting my cd rom drive and remounting, searching now. Sorry to use the forums as my documentation. Nice way to stay up top though.

---

### Post by oldos2er on 2009-04-08
Can you post output from the command
```
cat /etc/fstab
```
?

---

### Post by dokdoom on 2009-04-08
> **oldos2er said:**
> Can you post output from the command
```
cat /etc/fstab
```
?

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=59c82e23-e110-42f9-a84a-a1f23effe555 /               ext3    relatime,errors=remount-ro 0       1
# /dev/mapper/vg-home
UUID=6a0fdcbd-11a7-43a9-be4f-d7521dc799e3 /home           xfs     relatime        0       2
# /dev/mapper/vg-tmp
UUID=0dd6ff4e-303a-4777-b238-ee7db3cf44f3 /tmp            xfs     relatime        0       2
# /dev/mapper/vg-usr
UUID=953a2b55-724e-4c83-9b90-f69d169bc6c8 /usr            xfs     relatime        0       2
# /dev/mapper/vg-var
UUID=942df03d-327c-48f6-b160-8a621bd221eb /var            xfs     relatime        0       2
# /dev/mapper/vg-swap
UUID=70fdc6af-b4c4-46f8-b46a-c0f08c44e081 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by dokdoom on 2009-04-08
So I put in a few dvds, nothing worked past the dvd menu (another issue.) but when I put in a blank dvd nothing shows up and dmesg says:

```
[ 3154.196545] Buffer I/O error on device sr0, logical block 3956614
[ 3154.200807] end_request: I/O error, dev sr0, sector 15826456
[ 3154.200815] Buffer I/O error on device sr0, logical block 3956614
[ 3175.021422] end_request: I/O error, dev sr0, sector 15826456
[ 3175.021435] Buffer I/O error on device sr0, logical block 3956614
[ 3175.025910] end_request: I/O error, dev sr0, sector 15826456
[ 3175.025918] Buffer I/O error on device sr0, logical block 3956614
[ 3351.687436] end_request: I/O error, dev sr0, sector 15826456
[ 3351.687449] Buffer I/O error on device sr0, logical block 3956614
[ 3351.693004] end_request: I/O error, dev sr0, sector 15826456
[ 3351.693012] Buffer I/O error on device sr0, logical block 3956614
[ 4133.312224] cdrom: This disc doesn't have any tracks I recognize!
```

---

### Post by dokdoom on 2009-04-08
I smell a reinstall :(

---

### Post by oldos2er on 2009-04-08
"Buffer I/O error on device sr0"

 One explanation for the above error is a failing CD/DVD drive. If that's the case, reinstalling won't change anything. Maybe someone else knows another possible reason for that error; unfortunately, I don't.

---

### Post by dokdoom on 2009-04-09
> **oldos2er said:**
> "Buffer I/O error on device sr0"

 One explanation for the above error is a failing CD/DVD drive. If that's the case, reinstalling won't change anything. Maybe someone else knows another possible reason for that error; unfortunately, I don't.

Thank you very much for your assistance with this issue of mine. I did an install and everything is fine. I admit that error, when other people were getting the same one replaced their hardware to fix the problem. I thought I was gonna have to mail in my laptop :D. Fresh install, everything works as it should. 

My lesson I learned was don't change permissions (Or anything!) without properly documenting what you did. 

Thanks again!!!

---

