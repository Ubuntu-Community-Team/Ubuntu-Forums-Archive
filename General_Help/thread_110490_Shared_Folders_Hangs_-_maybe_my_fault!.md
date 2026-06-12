---
title: "Shared Folders Hangs - maybe my fault!"
date: 2005-12-30
forum: General Help
---

### Post by musther on 2005-12-30
I had NFS folder sharing working, (at least it seemed to be working, I never actually tested it from another machine).  Then I installed Samba, and went to the shared folders admin thingy to set up a shared folder, that was fine.  I closed the shared folder admin window, and then wanted to make a change, so I reopened it, but it just hung, so I had to kill it.  It now does this every time, and my file sharing definitely doesn't work.  This is the command line output:

```
root@dominus:/home/musther# shares-admin

(shares-admin:13417): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```

Cheers!

---

### Post by sciurus on 2005-12-31
Have you tried *sudo shares-admin*?

---

### Post by musther on 2005-12-31
I was logged in as root when I tried to run it, which should result in the same thing, but yes, I have done that.

---

### Post by newOldUser on 2006-01-04
I've been having a similar problem..... Shared Folders App is just hanging....

I tried the suggestion of: sudo shares-admin  from a terminal and got this error:

*** glibc detected *** double free or corruption (fasttop): 0x08259218 ***


It looks bad.  Any idea how to correct the error...

---

### Post by ZephyrXero on 2006-01-10
I'm having pretty much the same problem as well. I was trying to setup a NFS share and the machine I was attempting to mount it on was giving me an error about RPC not configured. I found somewhere on google that said to run rpc.mountd, and that would fix it. It did...kind of, I no longer got that error, but then it told me I did not have permission, so when I went back to the machine with the NFS share on it, and right clicked the folder and went to "share folder" nothing ever came up, then when I tried going to system>administration>shared folders it would come up and just freeze everytime. I've attempted stopping both my nfs daemon and my samba daemon and nothing seems to work.

When I ran it from the commandline I got this message:
```
*** glibc detected *** double free or corruption (fasttop): 0x08247718 ***
```

If it hasn't been done already, I'd like to file a bug report...but I'm not sure which program is at fault here.... any ideas?

---

### Post by pillypoon on 2006-02-13
I am also having the same problem.. Did anybody figure out the problem?

Thanks,
Pilly

---

### Post by sbassett on 2006-02-13
[QUOTE=ZephyrXero]I'm having pretty much the same problem as well. I was trying to setup a NFS share and the machine I was attempting to mount it on was giving me an error about RPC not configured. I found somewhere on google that said to run rpc.mountd, and that would fix it. It did...kind of, I no longer got that error, but then it told me I did not have permission, so when I went back to the machine with the NFS share on it, and right clicked the folder and went to "share folder" nothing ever came up, then when I tried going to system>administration>shared folders it would come up and just freeze everytime. I've attempted stopping both my nfs daemon and my samba daemon and nothing seems to work.

When I ran it from the commandline I got this message:
```
*** glibc detected *** double free or corruption (fasttop): 0x08247718 ***
```

If it hasn't been done already, I'd like to file a bug report...but I'm not sure which program is at fault here.... any ideas?[/QUOTE]


Zephyr -

I would say the share-admin is causing you the grief, and would be the best be to file the report against.

In the meantime, this quick little listing should help those with a little technical know-how.
[http://www.faqs.org/docs/securing/chap5sec33.html](http://www.faqs.org/docs/securing/chap5sec33.html)
This just gives the jist of the /etc/exports file for sharing via NFS.
Hopefully this will be fixed soon.

---

