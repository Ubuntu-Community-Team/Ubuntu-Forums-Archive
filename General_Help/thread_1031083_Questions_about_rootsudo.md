---
title: "Questions about root/sudo"
date: 2009-01-05
forum: General Help
---

### Post by kaoskorruption on 2009-01-05
Hi

I've been using sudo for a long time for various reasons (ie to open nautilus or gedit as root) and I've never had any problems - but today I used it to open firefox, googleearth, and vmware for different reasons to try to get them to work, and I've noticed that doing so sometimes messes up privillages that are difficult to put back.

Is it supposed to act like this? Is it generally bad to run things under sudo?

Thanks!

---

### Post by Carl Hamlin on 2009-01-05
> **kaoskorruption said:**
> Hi

I've been using sudo for a long time for various reasons (ie to open nautilus or gedit as root) and I've never had any problems - but today I used it to open firefox, googleearth, and vmware for different reasons to try to get them to work, and I've noticed that doing so sometimes messes up privillages that are difficult to put back.

Is it supposed to act like this? Is it generally bad to run things under sudo?

Thanks!

-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

I wouldn't necessarily say it's *bad* to run anything as root, but as you've already noticed, it certainly can affect permissions and privileges.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklhoIoACgkQyLm4ydrABvdSjgCeNrmSoPMA3Y4aL4hcG4Bbo4/e
Wu8An1RVl3YVESwrTdvUmfXmzXDVuuit
=SJe4
-----END PGP SIGNATURE-----

---

### Post by iaculallad on 2009-01-05
> **kaoskorruption said:**
> Hi

I've been using sudo for a long time for various reasons (ie to open nautilus or gedit as root) and I've never had any problems - but today I used it to open firefox, googleearth, and vmware for different reasons to try to get them to work, and I've noticed that doing so sometimes messes up privillages that are difficult to put back.

Is it supposed to act like this? Is it generally bad to run things under sudo?

Thanks!

I'd say you try reading on [Graphical Sudo]("http://www.psychocats.net/ubuntu/graphicalsudo"). Differences between using **sudo** and **gksudo** when running GUI applications which can lead to problems on privileges.

---

