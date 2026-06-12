---
title: "Permissions for uTorrent"
date: 2009-05-01
forum: General Help
---

### Post by GrimRe on 2009-05-01
Hi,

I'm having a small issue with my permissions for utorrent. Basically for whatever reason inside the utorrent client the files come up as "Error Access Denied"

Okay I thought, I'll just create a crontab under the root user to change the permissions of the files every day at 4am:

This is what I have:

```
0 4 * * * chmod -R 766 /var/shared/seeding
5 4 * * * chown -R myusername:myusergroup /var/shared/seeding
```

I'm running utorrent in myusername on system bootup. However, now when I try and navigate to the folder the permissions are set to:

list,create,delete/no access

???

---

### Post by SentientFluid on 2009-05-01
Is there a reason you're using /var?

Why not tell uTorrent to store things in your Home folder or a non-system related folder?

For example I have:

 /media/downloads
 /media/downloads/autostart
 /media/downloads/torrents
 /media/downloads/done

I download and save the .torrent files to /media/downloads/autostart.
uTorrent automatically loads them and copies them to /media/downloads/torrents.
Once they're done downloading, uTorrent moves the files to /media/downloads/done.

I suspect that Ubuntu or something may be doing some housekeeping and correcting the permissions on the folders in /var.  Mind you I could be wrong as I don't know what Ubuntu does for housekeeping on shutdown and startup.

Using /media (or something else) would bypass that.

---

### Post by michy99 on 2009-05-01
SentientFluid is right. By downloading to /var, you're creating way more problems than you need to. /var is a system folder and should be left alone.

---

### Post by GrimRe on 2009-05-02
ok thanks for that!

---

