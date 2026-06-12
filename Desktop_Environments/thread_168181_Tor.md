---
title: "Tor"
date: 2006-04-30
forum: Desktop Environments
---

### Post by rrz1989 on 2006-04-30
```

root@desktop:/home/ryan# tor
Apr 30 00:24:00.269 [notice] Tor v0.1.0.15. This is experimental software. Do not rely on it for strong anonymity.
Apr 30 00:24:00.303 [warn] /var/lib/tor is not owned by this UID (0). You must fix this to proceed.
Apr 30 00:24:00.303 [err] options_act(): Couldn't access/create private data directory /var/lib/tor
Apr 30 00:24:00.303 [err] init_from_config(): Acting on config options left us in a broken state. Dying.
root@desktop:/home/ryan# exit
exit
ryan@desktop:~$

```

Why am I getting this error, and how do I fix it?  This happens whether I am root or not.

---

### Post by j-strap2 on 2006-04-30
I take it you are using Breezy? Which Tor package are you using, the standard Ubuntu Breezy repository version?

The latest stable release of Tor is 0.1.0.17, which you should upgrade to. Go here:

[http://www.ubuntuforums.org/showthread.php?t=166988&highlight=tor](http://www.ubuntuforums.org/showthread.php?t=166988&highlight=tor)

---

### Post by rrz1989 on 2006-04-30
[QUOTE=j-strap2]I take it you are using Breezy? Which Tor package are you using, the standard Ubuntu Breezy repository version?

The latest stable release of Tor is 0.1.0.17, which you should upgrade to. Go here:

[http://www.ubuntuforums.org/showthread.php?t=166988&highlight=tor](http://www.ubuntuforums.org/showthread.php?t=166988&highlight=tor)[/QUOTE]

Alright, I added those two to /etc/apt/sources.list, and did:
```

sudo apt-get update
sudo apt-get upgrade

```
But yet I still get the same error when trying to run tor, or sudo tor.

---

### Post by j-strap2 on 2006-05-01
Ahhh. Tor should be running as a daemon by the init.d scripts. Kill all the tor processes you have run manually, then restart as a service:

sudo killall tor
sudo /etc/init.d/tor start

---

### Post by takayuki on 2006-05-04
thanks!  had the exact same problem and the update, then killall and start got it going just fine.

---

### Post by j-strap2 on 2006-05-04
Yes, updating Tor doesn't automatically restart the process, so unless you do this manually or reboot the machine, you still have the old version running.

---

