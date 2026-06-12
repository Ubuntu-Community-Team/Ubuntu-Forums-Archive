---
title: "Samba make all drives writable for both machines"
date: 2005-08-05
forum: Desktop Environments
---

### Post by DrQuincy on 2005-08-05
Hi

I have an XP machine and a Kubuntu machine connected to my Internet via a router.  I can view files from any hard drive on either machine via Samba but can't write to them.  How can I set up permissions so that I have full access on either machine to all the drives?  I'm not bothered about security because they're both on a LAN at home and only I use them.

Thanks.

---

### Post by Digitallysick on 2005-08-05
in windows you will have to select your C drive, and share, and setup the permissions, in ubuntu you will need to 

sudo gedit /etc/samba/smb.conf

at the bottom mine looks like this , i just drop files to my home folder, i guess to make the whole ubuntu drive writable you would probably path = /
in ubuntu you can also right click on the folder and setup permissions , i know its a pain in the @ss, it took me about 2 weeks to get it working right. but it will work 

# A sample share for sharing your CD-ROM with others.
;[cdrom]
; comment = Samba server's CD-ROM
; writable = no
; locking = no
; path = /cdrom
; public = yes

# The next two parameters show how to auto-mount a CD-ROM when the
# cdrom share is accesed. For this to work /etc/fstab must contain
# an entry like this:
#
# /dev/scd0 /cdrom iso9660 defaults,noauto,ro,user 0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
# is mounted on /cdrom
#
; preexec = /bin/mount /cdrom
; postexec = /bin/umount /cdrom


[Adam]
comment = Adams Home
path = /home/adam/
read only = no
inherit permissions = yes
case sensitive = no
msdfs proxy = no
delete readonly = yes
hide dot files = no

---

### Post by DrQuincy on 2005-08-06
Thanks for your help!  I added code similar to yout suggestion - I also had to set up advanced sharing on Ubuntu so I could share files outside of my home folder.

Thanks again.

---

### Post by Digitallysick on 2005-08-06
it took me forever, but i got it working, i network my mac g4 laptop to my ubuntu box i thought i would never get it to work, good luck! Now , if i could only print from my mac laptop, through ubuntu to my printer, that would be something sadly my 30 dollar lexmark doesnt have the best of functions

---

### Post by retsel on 2005-08-06
Not sure, but it sounds to me like you might have potential security problems with that setup when/if you log on to the Internt from XP. Sharing C probably isn't a good idea.

---

