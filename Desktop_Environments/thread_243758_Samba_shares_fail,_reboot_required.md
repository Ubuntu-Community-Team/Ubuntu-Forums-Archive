---
title: "Samba shares fail, reboot required"
date: 2006-08-25
forum: Desktop Environments
---

### Post by Switch625 on 2006-08-25
Hello all,

I'm having trouble with my samba shares. I've got two connections to different folders on the same drive of a remote Windows machine on the network, mounted under ```
/home/switch625/valjean
``` and ```
/home/switch625/networkdocs
```

The symptoms are that the share becomes inaccessible. Attempting to browse to the folders where they are mounted in any application causes that application to lock and have to be force-killed.
From the terminal, attempting to ls the contents of the share, or even tab-autocomplete the share name results in the terminal locking and having to be closed (Ctrl-C does not work).
Trying to unmount the share results in an error message such as ```
umount: /home/switch625/valjean: device is busy

```

This problem occurs after suspending or hibernating my machine (which I could live with if I had to), but more importantly, sometimes **for no reason whatsoever**. I stream music into Amarok from the "valjean" share so I know when it happens: suddenly the music will stop, Amarok will lock up, and the share will be unavailable as above. 
I've also had the networkdocs share lock up *just by having a file manager window looking at it*.

The only way to free the share is to reboot.
I should also point out that when one share locks up, it doesn't necessarily take down the other, so it doesn't seem to be a global smbfs thing.

Anybody got any ideas on how I can begin to troubleshoot this?

Using Xubutu 6.06.

Cheers,
Switch625

---

### Post by deltateam2 on 2007-02-22
i have the same problem.  i hope somebody can shed light on it

---

