---
title: "[SOLVED] Need Mount Particulars, please."
date: 2008-12-27
forum: General Help
---

### Post by Carl Hamlin on 2008-12-27
-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

I got some new SD for Christmas, which was working great.

I couldn't get it to come up in Partition Editor, however, which I figured had to do with the media type.

As an experiment, I went to the settings in the properties which come up from the shortcut on the desktop after the SD gets mounted, and chenged the filesystem type to 'ext3'.

Now, of course, it won't mount. However, when I went back and tried to mount it again as an msdos filesystem so I could take that flag off in the GUI, it wouldn't mount there, either.

Easy enough, thinks I, and restarts gnome to clear the flag *that* way.

Nope.

So. That was not as bright an idea as it seemed at the time. Where is that flag being saved, please? I'd like to be able to use my SD again.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklWjskACgkQyLm4ydrABvdjRACg2Jr1xR0TMSlu5vxajzPPAQc0
ut4AoMi4GccNOab2BBX60qx+z701QfGf
=D7GS
-----END PGP SIGNATURE-----

---

### Post by jnw222 on 2008-12-27
post output of 

sudo fdisk -l 


Lowercase L

---

### Post by Carl Hamlin on 2008-12-27
-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

Solved it - turns out I was being even dumber than I thought - must be coming down with a cold or something.

"gnome-mount -d /dev/mmcblk0p1" did the job nicely, and then I was able to pull the options off in the gui.

*facepalm*

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklWk2UACgkQyLm4ydrABvd6cACfbcjNFvF2rSdK2OOpxzJzik7w
QPcAn0zZTUZ4PAcOpD+5TBdsiHqU76F3
=tM38
-----END PGP SIGNATURE-----

---

### Post by jnw222 on 2008-12-27
btw what was up with the pgp message thing

---

### Post by Carl Hamlin on 2008-12-27
-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

That's a signed message. The hash will tell you whether or not the message has changed since I wrote it if you compare it against my public key.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklWnMsACgkQyLm4ydrABvfK8gCeJ4jbHAfAzgGn+F1B4naTUaTa
Rw8AmwRr1BqgImoIcKKjOzOHw0BvJwyO
=eY7U
-----END PGP SIGNATURE-----

---

