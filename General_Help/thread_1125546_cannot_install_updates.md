---
title: "cannot install updates"
date: 2009-04-14
forum: General Help
---

### Post by mitchell355zx on 2009-04-14
in the terminal it will not letme put password please help

---

### Post by skymera on 2009-04-14
When you type your password it does not show up on screen :)

So when you use sudo and enter your password, just type it an press return :)

---

### Post by Carl Hamlin on 2009-04-14
-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

Installing updates via the terminal requires the use of sudo. The commands you want to use are:

sudo apt-get update
sudo apt-get upgrade

The first time, it will ask you for a password. Barring the possibility that you've done a little experimenting, that's the password you're using to login.
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAknk6mkACgkQyLm4ydrABvcUBgCgy8Tv8Ay+vb86fLBWK/KCAxVK
7rYAoJR8q+5jxIMrjZhB9h9cd1qArVfP
=6DUg
-----END PGP SIGNATURE-----

---

