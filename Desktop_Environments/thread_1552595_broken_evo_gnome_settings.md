---
title: "broken evo gnome settings"
date: 2010-08-13
forum: Desktop Environments
---

### Post by dgermann on 2010-08-13
Hi--

In getting ready to upgrade from 8.04LTS to 10.04, I was playing around with my .gconf directory.

Here is what I did:
```
doug@doug2:~$ mv .gconf .gconf20100813
```
Then I logged out and back in.

Now I could not get evolution to work--when I clicked on the icon, it wants to set up a new email account, and will not recognize the ones already set up.

Also, the icons in the panel are strange, and most I had are no longer there.

So I restored sub directories from the backup to .gconf:
```
doug@doug2:~$ cp -a .gconf20100813/GNOME .gconf
doug@doug2:~$ cp -a .gconf20100813/schemas/ .gconf
doug@doug2:~$ cp -a .gconf20100813/system/ .gconf

```
...logging in and out after each command. Still evo does not recognize my email files.

Finally I restored my original .gconf:
```
doug@doug2:~$ sudo mv .gconf20100813/ .gconf
```

Still no evo! And then I completely rebooted the machine. Still no evo.

So, is there a way to get back all my email accounts and stored emails?

Any way to restore my prior settings in gnome in other places?

Thanks!

---

### Post by dgermann on 2010-08-13
Hi--

Never mind. I solved it.

When I copied back to the .gconf directory, I merely made the old settings (.gconf20100813) a subdirectory of the .gconf directory.

When I got that straight, all is well.

I should have realized....

Sorry for the false alarm. :oops:

---

