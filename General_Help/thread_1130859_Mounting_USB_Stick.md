---
title: "Mounting USB Stick"
date: 2009-04-20
forum: General Help
---

### Post by texas.chef94 on 2009-04-20
I am booted to sda1, inserted USB stick, red light flashes on stick but seemingly no entry. In terminal mount /dev/sda1 /mnt/usb-stick and response is allen@allen-desktop:~$ sudo mount /dev/sda1 /mnt/usb-stick
mount: mount point /mnt/usb-stick does not exist
allen@allen-desktop:~$
In the past all I needed to do was insert stick gain immediate access

Please advise and thank you

---

### Post by kpkeerthi on 2009-04-20
You might want to create the directory first:
```

sudo mkdir -p /mnt/usb-stick

```

---

### Post by daniel014 on 2009-04-20
I think there's a program called Mount Manager in the repositories.

---

### Post by texas.chef94 on 2009-04-20
Excuse ineptitude or comprehension challenge so let me have another go at this

Insert stick, red light flashes

sudo mkdir -p /mnt/usb-stick
creating directory

sudo mount /dev/sda1 /mnt/usb-stick

Response
allen@allen-desktop:~$ sudo mkdir -p /mnt/usb-stick
[sudo] password for allen: 
allen@allen-desktop:~$ sudo mount /dev/sda1 /mnt/usb-stick
mount: /dev/sda1 already mounted or /mnt/usb-stick busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt/usb-stick
allen@allen-desktop:~$ 

Before I would insert stick and contents would immediately open!
I am seeing nothing
Does it make a difference that I am booted to my HD, but also have an external and I am in Jaunty
I appreciate your time and effort

Allen

---

### Post by kpkeerthi on 2009-04-20
I wonder why Jaunty did not auto mount the stick. Do you have custom mount lines in /etc/fstab that prevents auto mounting?

You may try mounting it to /media instead.

1. sudo umount /mnt/usb-stick
2. sudo mkdir -p /media/usb-stick
3. sudo mount /dev/sda1 /media/usb-stick

The contents should open now. If not you can browse the contents, by pressing ALT+F2 and them type

nautilus /media/usb-stick

---

### Post by texas.chef94 on 2009-04-20
> **kpkeerthi said:**
> I wonder why Jaunty did not auto mount the stick. Do you have custom mount lines in /etc/fstab that prevents auto mounting?

You may try mounting it to /media instead.

1. sudo umount /mnt/usb-stick
2. sudo mkdir -p /media/usb-stick
3. sudo mount /dev/sda1 /media/usb-stick

The contents should open now. If not you can browse the contents, by pressing ALT+F2 and them type

nautilus /media/usb-stick
I did all three code, no errors and 11GB media icon popped up on the desk top.
When opened see URL
[http://s577.photobucket.com/albums/ss219/worthamtx/](http://s577.photobucket.com/albums/ss219/worthamtx/)
So anyway that is not what I need to mnt this stick.

Allen

---

### Post by calrogman on 2009-04-20
> **texas.chef94 said:**
> I am booted to sda1
So your USB stick is at /dev/sdb and the partition you want to mount is /dev/sdb1.

---

### Post by texas.chef94 on 2009-04-20
> **calrogman said:**
> So your USB stick is at /dev/sdb and the partition you want to mount is /dev/sdb1.

No quite the contrary. I am in sda1 Jaunty. However I do have an external drive.
I plugged my stick into USB while in SDA1 internal and in a effort to mount via suggestions I am ending up with an icon on desktop 12GB media which was on the URL and is not my USB stick

Allen

---

