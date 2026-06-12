---
title: "help install VLC 0.85"
date: 2006-08-30
forum: Desktop Environments
---

### Post by syxbit on 2006-08-30
it's not in the repo's
i can either install from source, or from a .deb
i found on the vlc website a nightly build
[http://nightlies.videolan.org/build/dapper-i386/vlc/0.8.5.final.1/](http://nightlies.videolan.org/build/dapper-i386/vlc/0.8.5.final.1/)
but towards the bottom, there are 2 files that appear the right one
one at 7.9m and the other at 8.0m
anyone know the difference, or which one i should get?
thanks

ps. i want it cause 0.85 has the 16:10 aspect ratio (same as my monitor) and 0.84 only has 16:9

---

### Post by Cable on 2006-08-30
Just add the VLC repo to your sources.list (located at /etc/apt/sources.list). If you look on the [VLC Nightly Builds]("http://nightlies.videolan.org/") page towards the bottom, you'll see that there is a Dapper repo.
```

deb http://nightlies.videolan.org/build/dapper-i386 /

```
 
Just add that to your sources.list and then import the gpg key like so...
```

gpg --keyserver subkeys.pgp.net --recv-keys 81CACA84
gpg --export 81CACA84 -a|sudo apt-key add -

```
 
Then
```

sudo apt-get update && sudo apt-get dist-upgrade

```
and it should say that VLC has an upgrade.

---

### Post by syxbit on 2006-08-30
thanks
i did it, and it showed installing  vlc 0.8.5.final.1-0ubuntu2 
which was available from that page.
should this update forever with newer builds in the future ?

---

