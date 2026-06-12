---
title: "Missing icons and files from ~/Desktop"
date: 2009-01-04
forum: General Help
---

### Post by ghstridr on 2009-01-04
Is there some setting in gnome that will hide objects saved to the Desktop folder?
If I look in the dir via a terminal, everything is there.
It just doesn't show up on the desktop itself.

---

### Post by cdaringe on 2009-01-04
hey there mate.

not quite sure.

but you may want to do a:
```

gconf-editor

```
then browse to apps->nautilus and browse those preferences.

see if that gets you anywhere?
sorry i couldn't add more.

---

### Post by ghstridr on 2009-01-05
Godd suggestion, but that wasn't the answer.  Thanks though!

---

### Post by Carl Hamlin on 2009-01-05
> **ghstridr said:**
> Is there some setting in gnome that will hide objects saved to the Desktop folder?
If I look in the dir via a terminal, everything is there.
It just doesn't show up on the desktop itself.

-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

I've had a similar problem occur while experimenting with the language settings. When it comes back up and wants to modify the names for the default directories, if you say no and leave the ones from the previous language, then 'Desktop' is no longer your desktop directory.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklhpbkACgkQyLm4ydrABvcHygCgl/6TX3Kkqo0XR8KlabtYJoKP
9WgAoJPZtM6jlZGfnrwx0f5DwWgKc/I6
=4Uun
-----END PGP SIGNATURE-----

---

### Post by ghstridr on 2009-01-06
Well, I finally fixed it.  I took a crazy leap of faith and was going to mark nautilus for a complete reinstall using synaptic.
So I fire up synaptic and find out that nautilus is not even installed!!!
One install and a reboot later....all is again good with my little world.

How in the world nautilus got uninstalled is a complete mystery to me.  Oh well, problem solved. Many thanks for the suggestions and the comments!

---

### Post by jms1989 on 2009-01-29
I don't mean to hijack the thread but I have a simular problem.

I opened the configuration editor from (Applications > System > Configuration Editor).
I navigated to apps/nautilus/preferences.
I found a unchecked the setting to show desktop.
I works but now I can't get it back without loging out or rebooting.

Check and uncheck has no efect. What happened?

---

