---
title: "gam_server and umount"
date: 2005-07-17
forum: Desktop Environments
---

### Post by pabc on 2005-07-17
After *much* mucking around compiling mplayer from source because of apt-gets version having flaky a52 / ac3 support I finally get around to watching a DVD.

After I've finished I find I can't eject the DVD. Having a google it appears that this can only be the case if the resource is being accessed.

[COLOR=Blue]fuser -c /dev/cdrom[/COLOR]

reports PID 6426 is the guilty process.

[COLOR=Blue]ps aux | grep 6426[/COLOR]

shows gam_server is accessing the drive stopping me unmounting via normal means (yes, I know umount -l /dev/cdrom will do it but it's hardly ideal)

So, any ideas on what gam_server is doing trying to monitor changes on a read-only device and is there anyway I can config it not to bother?

P

---

### Post by pabc on 2005-07-18
searching is such a wonderful idea....

[http://ubuntuforums.org/showthread.php?t=19331&highlight=gamin](http://ubuntuforums.org/showthread.php?t=19331&highlight=gamin)

P

---

### Post by poptones on 2005-07-18
But that doesn't really solve your problem, does it?

I thought of replying to you earlier, but it seemed odd to me a system would even be doing this so I thought perhaps a dev might respond. 

[http://www.ubuntuforums.org/showthread.php?t=31819](http://www.ubuntuforums.org/showthread.php?t=31819)

There's an explanation on that page that should give you a good workaround.

---

### Post by pabc on 2005-07-18
opps - the post you linked to was the one I meant to - doh!

I'll just set up a ~/.gaminrc to poll /cdrom and hopefully that will sort it.

Cheers

P

---

