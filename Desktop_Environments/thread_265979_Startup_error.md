---
title: "Startup error"
date: 2006-09-26
forum: Desktop Environments
---

### Post by Magiczero on 2006-09-26
Hello

When i started my computer today it got passed everything up until the point were it does the Filesystem check and it went to a screen that said 
> Filesystem system check failed:  Please repair manually

I need help!  I don't know how to fix this!!  

Can Someone help?

Thanks

I hit ctrl+d to get past that error

---

### Post by pseudonym on 2006-09-26
Looks like some filesystem corruption might have crept onto your hard drive (power outage perhaps?) Don't sweat it, though, it's usually reparable.

Boot into recovery mode and see what happens. Even if you don't get any errors you should fire up a live cd and do a filesystem check from that.

What filesystem are you using? ext3? reiserfs? From a console in the live cd you can run filesystem repair programs like fsck (ext2/3) and reiserfsck (reiserfs). Check the manual pages first before doing so - to know what options to use as well as to understand what's going on.

---

