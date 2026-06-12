---
title: "hang when accessing a mounted snap server share"
date: 2005-11-17
forum: Desktop Environments
---

### Post by Arthur_Dent on 2005-11-17
When I mount my [snap server 2000]("http://www.digit-life.com/articles/quantumsnapserver/") and browse a few folders the computer fully locks up. The keyboard, mouse and gui lockup, the only thing I can do is reset the power.

/var/log/kern.log has this error
localhost kernel [4295001.282000] smb_proc_readdir_long: error=-2, breaking

My /etc/fstab 
```

//10.0.0.254/Backup /media/SnapServer smbfs credentials=/root/.smb-snap-credentials,dmask=777,fmask=777 0 0
```

snap server 2000
snap os Server v3.4.770

smbfs 3.0.14a-6ubuntu1
samba 3.0.14a-6ubuntu1
linux-image-2.6.12-9-686

-kbrosnan

---

### Post by HermanAB on 2005-11-17
Hmm, I would recommend that you don't mount it.  Use the smbclient and Konqueror smb:// ioslave till you figured out what ails it.

See this:
[http://www.aerospacesoftware.com/samba-debug-howto.html](http://www.aerospacesoftware.com/samba-debug-howto.html)

and this:
[http://www.aerospacesoftware.com/samba-ssh-tunnel-howto.htm](http://www.aerospacesoftware.com/samba-ssh-tunnel-howto.htm)

Cheers,

Herman

---

