---
title: "Replace Kubuntu boot-screen with Ubuntu?"
date: 2006-08-14
forum: Desktop Environments
---

### Post by petersjm on 2006-08-14
Hi guys. After hearing some nice things about Kubuntu I decided to download it over Ubuntu by using:

```
sudo aptitude install kubuntu-desktop
```

Which all worked perfectly well. So I rebooted and logged in with KDE under Sessions, had a play around with it, decided I didn't like it and would just stick to Gnome. I logged out and back in with Gnome, headed back to the terminal and typed:

```
sudo aptitude purge kubuntu-desktop
```

and, as expected, it deleted all its dependancies, too. Nice, I thought. *But* now the boot-sequence (I mean where it loads the drivers and kernel and stuff, not grub) is still showing Kubuntu instead of Ubuntu.

It's a minor annoyance, but I'd rather get back my Ubuntu boot-sequence (or whatever it's called) if it's at all possible. Does anyone know a way? Thanks in advance.

---

### Post by iamhugeinjapan on 2006-08-14
Your offending package is kubuntu-artwork-usplash, is it still installed?

---

### Post by ozorba on 2006-08-14
Re-install ubuntu-artwork-usplash and you get it back.

---

### Post by visik7 on 2006-08-14
```
sudo update-alternatives --config usplash-artwork.so
```

---

### Post by petersjm on 2006-08-14
Many thanks, guys. :KS I'll check this evening when I'm home from work. Strange, though, as I'm *almost* convinced that it listed kubuntu-artwork-usplash in the remove list when I purged it. Unless there was some other usplash package it removed...

---

### Post by Jucato on 2006-08-14
just to add to visik7's instructions:

1. run the command
```
sudo update-alternatives --config usplash-artwork.so
```

And choose the one called ubuntu-artwork.so

2. run

```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

to update your linux image to display the proper USplash

---

### Post by petersjm on 2006-08-14
Thanks, Fenyx. I'll give it a go this evening.

---

### Post by petersjm on 2006-08-14
> **Fenyx said:**
> just to add to visik7's instructions:

1. run the command
```
sudo update-alternatives --config usplash-artwork.so
```

And choose the one called ubuntu-artwork.so

2. run

```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

to update your linux image to display the proper USplash

Hmmm. Seems I've hit a problem. When running the first terminal command above, I get:

```
There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-default.so). Nothing to configure.

```

And when I try to reinstall ubuntu-artwork-usplash, it says it can't find it, but can find other packages with that in the name (i.e. kubuntu-art... xubuntu-art...). And

```
sudo aptitude purge kubuntu-artwork-usplash
```

does nothing. Does anyone have a clue what I can do to solve this?

** EDIT :: FIXED ** While the first command gave the error outlined above, I ran the second command anyway, and it fixed the problem! Thanks all for your suggestions and support! :D

---

