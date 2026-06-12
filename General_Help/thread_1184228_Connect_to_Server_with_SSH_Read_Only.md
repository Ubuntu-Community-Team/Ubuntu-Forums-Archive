---
title: "Connect to Server with SSH Read Only"
date: 2009-06-10
forum: General Help
---

### Post by DGortze380 on 2009-06-10
Hey All,

Been searching around but can't quite find what I need.

I'm looking to do two things.

1) I need to use the Connect to Server App to Connect to a machine via SSH. I'd like this happen automatically on log-in, anyway to do that?

2) I'd really like the folder to mount read only when I connect above. Possible? How?

Thanks in advance.

---

### Post by DGortze380 on 2009-06-10
Ok, got it to connect and mount using sshfs. 

Is it possible to use sshfs to mount it read-only?

Am I correct in assuming I can use a simple start-up script to mount it on start-up?

---

### Post by dmizer on 2009-06-10
A couple of things.

If you just want a read only share, SSH probably isn't the tool you need. Something like trying to kill a fly with a swiss army knife.

Also, you seem to want more refined control than the "Connect to server" app will provide. If you're dead set on SSH, you'll probably have to mount in /etc/fstab to get the kind of control you want.

SFTP may give you what you need (makes use of SSH and the "connect to server" tool, and r/w permissions can be handled on the server side): [http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)

---

### Post by DGortze380 on 2009-06-10
> **dmizer said:**
> A couple of things.

If you just want a read only share, SSH probably isn't the tool you need. Something like trying to kill a fly with a swiss army knife.

Also, you seem to want more refined control than the "Connect to server" app will provide. If you're dead set on SSH, you'll probably have to mount in /etc/fstab to get the kind of control you want.

SFTP may give you what you need (makes use of SSH and the "connect to server" tool, and r/w permissions can be handled on the server side): [http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)

I agree, ssh appears to be more than I need for this one issue.

It's a long explanation, but I do need more functionality than just an Read-Only Share ... easier and more secure for me to use ssh for everything.

As far as the Read-Only part, sshfs worked fine.

[CODE]
sshfs user@host:folder mountPoint -o ro
[CODE]

I believe this can also be added to fstab, I'll update if fstab works

---

### Post by dmizer on 2009-06-11
I believe you'll need to include fuse to mount ssh shares via fstab. I still think that sftp will do what you need and give you lots of security in the process. Though I admitedly don't know exactly what you need, but your line will look something like this:
```
sshfs#user@host:/folder /mountPoint fuse defaults,ro 0 0
```

Be aware of this: [https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/243298](https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/243298)

---

### Post by DGortze380 on 2009-06-11
Finally got my RSA issues worked out.

Ended up using a script instead of fstab, not the best way but give me more flexibility.

Working now. Thanks for the advice.

---

