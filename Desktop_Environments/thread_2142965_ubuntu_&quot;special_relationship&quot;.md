---
title: "ubuntu &quot;special relationship&quot;"
date: 2013-05-07
forum: Desktop Environments
---

### Post by Swiftjay on 2013-05-07
Ubuntu and me seem to have a special relationship from my previous laptop to my current one now.

I'm on a toshiba satellite A660 now with a nvidia (non optimus unlike my previous DELL one...)

I did a fresh install of Ubuntu 13.04 64-bit (didn't need to worry about uefi mode luckily even though I had windows 8 dual boot).

However when I shut down it says

 ```
rpcbind: restarted terminating with rpcbind -w
```

Everything unmounts except for / which is busy then I have to manually shut down.

Today it wouldn't boot into the gui at all, it would say reverting to power saving mode (didn't screen shot unfortunately).

When powering off I got 

```
/var/lib/unreadahead/debugfs busy - remounted read only
* unmounting local filesystems..
umount: /run/lock : not mounted
umount: /run/shm: not mounted
```

I have to boot into recover mode then log under root and do startx to load up the gui from root, after resuming booting I could then log in.

I'm a very stubbourn guy I like using ubuntu and probably regardless of this frustration I'm still going to use it cause I like it.  However any help to make life a bit more painless when booting up and shutting down would be appreciated beyond belief.  More then willing to provide logs or other stuff anyone wants/needs to help diagnose this.

Regards,
James

---

