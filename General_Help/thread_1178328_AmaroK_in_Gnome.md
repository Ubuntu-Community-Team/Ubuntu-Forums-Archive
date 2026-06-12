---
title: "AmaroK in Gnome"
date: 2009-06-04
forum: General Help
---

### Post by bruno9779 on 2009-06-04
AmaroK in gnome won't install unless kubuntu-restricted-extras is installed too.

The .deb for Ubuntu should resolve this dependency, but it doesn't. A lot of people have already had this problem

Shold i report this as a bug? If yes, to Canonical or to Amarok? How do i find out who the maintainer of a package is?

---

### Post by Yellow Pasque on 2009-06-04
I can't reproduce this issue and I don't see where kubuntu-restricted-extras is a dependency of amarok. Are you using a .deb from the Ubuntu repos or elsewhere?

---

### Post by bruno9779 on 2009-06-10
What i mean, is that with the new Amarok, Ubuntu-restricted-extras does not work.

If i want to listen to MP3 in ubuntu i have to install Kubuntu-restricted-extras

---

### Post by hibliss on 2009-06-10
> **bruno9779 said:**
> What i mean, is that with the new Amarok, Ubuntu-restricted-extras does not work.

If i want to listen to MP3 in ubuntu i have to install Kubuntu-restricted-extras

I had issues with Amarok and switched to Banshee. [http://banshee-project.org/]("http://banshee-project.org/")

I think as a whole, they are comparable, and Banshee has given me no issues.

---

### Post by Yellow Pasque on 2009-06-10
> What i mean, is that with the new Amarok, Ubuntu-restricted-extras does not work.

Amarok uses the Phonon extraction layer, which uses phonon-backend-xine by default. xine needs libxine1-ffmpeg to play mp3's, which is one of the packages pointed to by kubuntu-restricted-extras.

If you don't want to use xine or have kubuntu-restricted-extras installed, install phonon-backend-gstreamer and set phonon to use gstreamer with the following command:
```
qtconfig
```

---

