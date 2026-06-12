---
title: "Using IMage from SMB Share as Desktop Background"
date: 2007-08-20
forum: Desktop Effects &amp; Customization
---

### Post by Catsworth on 2007-08-20
Hi Guys,

I've got a small NAS running on my home network, this NAS is setup as a bookmark and appears in the 'Places' directory.

I have some images on there that I would like to be able to use as desktop backgrounds, but when I try to navigate to them the locations are unavailable from the desktop background chooser.

Is there a way around this, or a way to correct this problem?

Thanks.

---

### Post by jakev383 on 2007-08-20
How are you mounting the share?

---

### Post by Catsworth on 2007-08-20
Got a shortcut on the desktop that I created in the 'Connect to a Server' option in the 'Places' menu.

---

### Post by jakev383 on 2007-08-22
> **Catsworth said:**
> Got a shortcut on the desktop that I created in the 'Connect to a Server' option in the 'Places' menu.

That way (as you know) won't work.  You need to mount it in your /ets/fstab .  Here's how I mount a share off of my server, which is served via Samba (note that CIFS is much faster than SMBFS).  These lines are in my /etc/fstab (also note that my share is NOT user/pass protected):

```

//192.168.76.1/HomeShare     /media/HomeShare     cifs     guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm     0 0

```

192.168.76.1 is my home server that serves the /HomeShare.  /media/HomeShare is a dir I created to mount the share to (and it's in /media so it shows on my desktop as a drive).  The rest is info for the system to know how to mount it.  I'm assuming since it's a NAS that it supports Windows file sharing.
Hope that helps!

---

### Post by airtonix on 2007-09-14
If your NAS uses NFS then use that instead....

I see speed improvements of 2/3mb per sec over smb.

---

