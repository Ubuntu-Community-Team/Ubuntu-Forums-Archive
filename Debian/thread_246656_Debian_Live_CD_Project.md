---
title: "Debian Live CD Project"
date: 2006-08-29
forum: Debian
---

### Post by tturrisi on 2006-08-29
This has been around for a bit.
However I could never get past the login on the live cds and today downloaded from the mirror site and was able to login and then change the password.  This is a sweet way to test out pure Debian for those who want to try it.

Project Homepage:
[http://debian-live.alioth.debian.org/](http://debian-live.alioth.debian.org/)

Downloads (usable):
[http://ftp.ch.debian-unofficial.org/live-cd/current/i386/](http://ftp.ch.debian-unofficial.org/live-cd/current/i386/)

Wiki:
[http://live.debian.net/wiki/](http://live.debian.net/wiki/)

Change password:

The wiki says that the default username & pasword are debian & debian.  But the sid iso at the above download has a default username as "casper" and the password is not knowable, thus one will need to change the password to be able to access administrative programs & tools like so:
```
ctrl+alt+F2
sudo passwd
type new password at prompts
ctrl+alt+F7
```

You can even use a boot option to install to hard drive.

---

### Post by deanlinkous on 2006-08-29
The cool thing IMO about the live project is rolling your own...
[http://live.debian.net/wiki/ISO_Howto](http://live.debian.net/wiki/ISO_Howto)

---

