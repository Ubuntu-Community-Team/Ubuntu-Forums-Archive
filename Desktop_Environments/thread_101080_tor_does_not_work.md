---
title: "tor does not work"
date: 2005-12-09
forum: Desktop Environments
---

### Post by montes.c on 2005-12-09
```
xochiyotl% tor
Dec 08 22:42:56.411 [notice] Tor v0.1.0.15. This is experimental software. Do not rely on it for strong anonymity.
Dec 08 22:42:56.412 [warn] /var/lib/tor is not owned by this UID (1000). You must fix this to proceed.
Dec 08 22:42:56.412 [err] options_act(): Couldn't access/create private data directory /var/lib/tor
Dec 08 22:42:56.412 [err] init_from_config(): Acting on config options left us in a broken state. Dying.
xochiyotl% su
Password: 
xochiyotl# tor
Dec 08 22:43:06.891 [notice] Tor v0.1.0.15. This is experimental software. Do not rely on it for strong anonymity.
Dec 08 22:43:06.892 [warn] /var/lib/tor is not owned by this UID (0). You must fix this to proceed.
Dec 08 22:43:06.892 [err] options_act(): Couldn't access/create private data directory /var/lib/tor
Dec 08 22:43:06.893 [err] init_from_config(): Acting on config options left us in a broken state. Dying.

```

I installed tor through synaptic and it says this.

---

### Post by montes.c on 2005-12-17
Some help please?

---

### Post by azcrumpty on 2005-12-17
It seems like tor isn't starting as the debian-tor user.

Try:

sudo -u debian-tor /etc/init.d/tor start

or 

sudo /etc/init.d/tor start

If those fail

Note that tor is not changing or trying to to change to the debian-tor user id.  It seems to be using your account.

You can also try

sudo -u debian-tor tor

Or just ls -ls /var/lib and see what user owns tor.

Let's say it is user pete.

You could just

sudo -u pete tor

But the run as user must match that path.


[QUOTE=montes.c]```
xochiyotl% tor
Dec 08 22:42:56.411 [notice] Tor v0.1.0.15. This is experimental software. Do not rely on it for strong anonymity.
Dec 08 22:42:56.412 [warn] /var/lib/tor is not owned by this UID (1000). You must fix this to proceed.
Dec 08 22:42:56.412 [err] options_act(): Couldn't access/create private data directory /var/lib/tor
Dec 08 22:42:56.412 [err] init_from_config(): Acting on config options left us in a broken state. Dying.
xochiyotl% su
Password: 
xochiyotl# tor
Dec 08 22:43:06.891 [notice] Tor v0.1.0.15. This is experimental software. Do not rely on it for strong anonymity.
Dec 08 22:43:06.892 [warn] /var/lib/tor is not owned by this UID (0). You must fix this to proceed.
Dec 08 22:43:06.892 [err] options_act(): Couldn't access/create private data directory /var/lib/tor
Dec 08 22:43:06.893 [err] init_from_config(): Acting on config options left us in a broken state. Dying.

```

I installed tor through synaptic and it says this.[/QUOTE]

---

