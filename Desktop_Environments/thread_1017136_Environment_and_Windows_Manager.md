---
title: "Environment and Windows Manager"
date: 2008-12-20
forum: Desktop Environments
---

### Post by aculade on 2008-12-20
I've been searching for a while now and there's something I can't quite figure out...

Is it possible to have Gnome as the desktop environment and let Xfce just manage the windows? Everything I've seen just says how to select the environment at login. Been there, done that...not exactly what I want though.

I want gnome...all of the ubuntu default programs etc...but I like the themes and how easy it is to manage window styles in xubuntu. Is there any way to get the best of both worlds?

Thanks for any help!

---

### Post by Carl Hamlin on 2008-12-20
-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

I'd make a list of the utilities I like in Gnome, install XFCE and them manually add those utilities in after the fact and see if they run properly. So far as running to desktop environments simultaneously, I think you're not going to get much help there - on a code level it would be like the two environments were stepping on one another's toes.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklNh/cACgkQyLm4ydrABvdaIgCfQJfdFDcQX4lZi67qFlCWAjpZ
Uh8An2pUrUscwCi8CEc9vg5gbVPqnlXw
=GO9i
-----END PGP SIGNATURE-----

---

### Post by ugm6hr on 2008-12-20
> **aculade said:**
> I want gnome...all of the ubuntu default programs etc...but I like the themes and how easy it is to manage window styles in xubuntu. Is there any way to get the best of both worlds?

The Window Manager is xfwm4 in XFCE.

So, in theory (I have never done this):

```
sudo apt-get install xfwm4
xfwm4 --replace
```

You might also want: xfce4-mcs-manager & xfwm4-themes

Hope that's enough to get you started...

---

