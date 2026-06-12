---
title: "Log In as &quot;root&quot;"
date: 2009-01-11
forum: General Help
---

### Post by oldtraveler on 2009-01-11
In my new installation of Ubuntu 8.10 I don't recall any option to set up "root" user.  Thus I only have my user name and password. I apparently need to log in as "root" in order to mount other volumes (Windows).  How can I log in as "root" and once there what password should I try?

---

### Post by Carl Hamlin on 2009-01-11
-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

Righto. In order to run commands as root, prepend them with 'sudo'. When it asks for a password, it's the one you use to login.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklqf9YACgkQyLm4ydrABvfiZQCfQj/BwRP5/u58ldrYvQ7QnsE8
lnAAoKr5fVtwZWq09zYt0nofgWafvX6t
=BrWW
-----END PGP SIGNATURE-----

---

### Post by oldtraveler on 2009-01-11
That solved it.  Thank You.

---

### Post by cariboo on 2009-01-11
ehorton: It is against forum policy to instruct someone on how to enable the root user. Please refer anyone that wants to log in as root to have a look at this [page]("http://help.ubuntu.com/community/RootSudo").

Jim

---

### Post by Carl Hamlin on 2009-01-11
> **ehorton said:**
> Once you have completed the new install of 8.1, you really need to set the root password.

-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

Why? Sudo does the job quite well and doesn't expose you to the added security risks inherent in having an enabled root account.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklqtxIACgkQyLm4ydrABvf1agCcDnyk0rf3v7OAC6xmCFEYVwCJ
RSoAoJI5wG04DseHp7d6mOGhd3SeFA7M
=DTUU
-----END PGP SIGNATURE-----

---

### Post by tuxxy on 2009-01-11
> **Carl Hamlin said:**
> -----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

Why? Sudo does the job quite well and doesn't expose you to the added security risks inherent in having an enabled root account.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklqtxIACgkQyLm4ydrABvf1agCcDnyk0rf3v7OAC6xmCFEYVwCJ
RSoAoJI5wG04DseHp7d6mOGhd3SeFA7M
=DTUU
-----END PGP SIGNATURE-----

Whether the root account is disabled or not its still their as you can run command with admin privs.

---

### Post by Carl Hamlin on 2009-01-11
> **cariboo907 said:**
> It is against forum policy to instruct someone on how to enable the root user.

-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

Jim:

I'm having trouble locating that edict in the posted forum policies. Can you please let me know where I could find that?

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklquIUACgkQyLm4ydrABvcuOgCgtGamSXXRbr9qtKt6Rf4xO/aT
4vQAnRxeKbNUOqqHPdMVd41jlmdlYGNt
=DfsI
-----END PGP SIGNATURE-----

---

### Post by Carl Hamlin on 2009-01-11
> **tuxxy said:**
> Whether the root account is disabled or not its still their as you can run command with admin privs.

-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

I concur, however disabling root login makes external attacks over the internet a more difficult prospect.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklquQEACgkQyLm4ydrABveWTgCfe/GaBYyGgTSaapGbBHuboqph
NzYAn1mItZKMeDw1s09vMJaih744t1JI
=z44s
-----END PGP SIGNATURE-----

---

### Post by overdrank on 2009-01-11
> **Carl Hamlin said:**
> -----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

Jim:

I'm having trouble locating that edict in the posted forum policies. Can you please let me know where I could find that?

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklquIUACgkQyLm4ydrABvcuOgCgtGamSXXRbr9qtKt6Rf4xO/aT
4vQAnRxeKbNUOqqHPdMVd41jlmdlYGNt
=DfsI
-----END PGP SIGNATURE-----

[Forums Ploicy]("http://ubuntuforums.org/showthread.php?t=716201")

---

### Post by Carl Hamlin on 2009-01-11
-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

Thank you, overdrank. I was looking here:

[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

I'm surprised at this decision, but I understand the rationale from the perspective of the policy authors.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklqvGcACgkQyLm4ydrABveuTwCg23djqnRt/AB8DuZkWteKXZu4
KUkAn31TUPycvpnPW8pcbZEYR7hHy612
=jxxq
-----END PGP SIGNATURE-----

---

