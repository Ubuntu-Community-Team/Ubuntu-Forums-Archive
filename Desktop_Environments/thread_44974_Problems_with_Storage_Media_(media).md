---
title: "Problems with Storage Media (media:/)"
date: 2005-06-28
forum: Desktop Environments
---

### Post by haaglin on 2005-06-28
Hi. Can anyone please tell me how i can get my cd-drives back in media:/? i only have my harddrives there, and i cant figure out how to get my cd-drives back there, and i know they are suppose to, because all of my friends with kubuntu have their cd-roms there. 

Anyone, Please help me with this issue.

also, i cant get ivman to work, i get this error: 

> 
 Ikke's Volume Manager, [http://ivman.sf.net](http://ivman.sf.net)
10334: arguments to dbus_message_new_method_call() were incorrect, assertion "path != NULL" failed in file dbus-message.c line 1723.
This is normally a bug in some application using the D-BUS library.
libhal.c 1856 : Couldn't allocate D-BUS message


---

### Post by Takis on 2005-06-28
We-ell I can help with the first bit: I think media:/ only shows the cd drive when there's a cd in there (not necessarily mounted, though).

---

### Post by haaglin on 2005-06-28
[QUOTE=Takis]We-ell I can help with the first bit: I think media:/ only shows the cd drive when there's a cd in there (not necessarily mounted, though).[/QUOTE]

i know, but it isnt there even when there is a cd in the drive, or when it is mounted.

---

### Post by haaglin on 2005-06-30
Removable drives works fine btw, it is just my cd-rw and dvd-rw drives that isn't listed in media:/

this is what is listed in my fstab, maybe the problem is there? 

> 
/dev/hdc        /media/cdrom0   udf,iso9660	ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660	ro,user,noauto  0       0


---

### Post by Takis on 2005-06-30
No, those fstab entries look fine. Hmm.
Do you need them to appear in media:/, though?

---

### Post by haaglin on 2005-07-01
[QUOTE=Takis]No, those fstab entries look fine. Hmm.
Do you need them to appear in media:/, though?[/QUOTE]
Well, i'm tired of manually mount them all the time, and have to go into the mountpoints to access them.

---

### Post by fdoving on 2005-07-01
[QUOTE=haaglin]Well, i'm tired of manually mount them all the time, and have to go into the mountpoints to access them.[/QUOTE]
 try remove the entries from /etc/fstab.

- Frode

---

### Post by haaglin on 2005-07-01
[QUOTE=fdoving]
try remove the entries from /etc/fstab.

- Frode
[/QUOTE]
Now everything is gone from media:/:?

---

### Post by fdoving on 2005-07-01
[QUOTE=haaglin]Now everything is gone from media:/:?[/QUOTE]
 Ok. put them back then :)

---

### Post by haaglin on 2005-07-01
[QUOTE=fdoving]Ok. put them back then :)[/QUOTE]
i did  ;-)  tnx anyway

---

### Post by chandra on 2005-07-01
I had a similar problem on one PC but not another.  I opened Konqueror and hit F9 but the CD-RW and DVD drives did not appear under media:/.

On a konsole, I then typed

mount /media/cdrom0

and automagically, the media:/ of Konqueror was refreshed and I could access the CD/DVD drives on Konqueror from then on.  Perhaps you could also try this.

I do not know if this is a KDE bug.

---

### Post by haaglin on 2005-07-02
no, still not in media:/  ](*,)

---

### Post by t2kburl on 2005-07-02
just a wild guess ...
I had to do this after booting into windows to get my windows partitions back into media where I had previously put them ...

try this

sudo mkdir /media/cdrom0
sudo mkdir /media/cdrom1

then remount your fstab with 

sudo mount -a

worked for me to get my win parts back

---

