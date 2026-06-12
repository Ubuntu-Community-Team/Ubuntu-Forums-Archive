---
title: "Keeping the Ubuntu Boot screen when Installing Kubuntu as well"
date: 2006-06-27
forum: Desktop Environments
---

### Post by Devilotx on 2006-06-27
I'm currently running Ubuntu on my laptop, and I have a need for KDE on here as well, but I know from past installs that if I simply issue a sudo apt-get install kubuntu-desktop, I'll get kubuntu, but the boot screen will also change from ubuntu to kubuntu.

the screen I'm talking about is after the grub menu where you see the services starting below an ubuntu logo, well I'd like that to stay ubuntu rather then change to kubuntu after I install it.

any advice?

---

### Post by knn on 2006-06-27
[QUOTE=Devilotx]I'm currently running Ubuntu on my laptop, and I have a need for KDE on here as well, but I know from past installs that if I simply issue a sudo apt-get install kubuntu-desktop, I'll get kubuntu, but the boot screen will also change from ubuntu to kubuntu.

the screen I'm talking about is after the grub menu where you see the services starting below an ubuntu logo, well I'd like that to stay ubuntu rather then change to kubuntu after I install it.

any advice?[/QUOTE]

type this in terminal:
```
 sudo update-alternatives --config usplash-artwork.so 
```

and select usplash-default.

---

### Post by shane2peru on 2006-06-27
This didn't seem to fix mine.  It appears as though the other themes are not installed.  Here is what I see:
```

There are 4 alternatives which provide `usplash-artwork.so'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/lib/usplash/usplash-default.so
 +    2        /usr/lib/usplash/kubuntu-splash.so
      3        /usr/lib/usplash/xubuntu-splash.so
*     4        /usr/lib/usplash/edubuntu-splash.so

Press enter to keep the default[*], or type selection number:

```  notice that the + is by the kubuntu-splash.so  that is what it seems to be using.  It has the * by the edubuntu-splash.so , however nothing changed.  Help.  How can I install these?

Shane

---

### Post by shane2peru on 2006-06-27
Well, I take that back.  I get the Ubuntu when logging off and the Kubuntu when booting up.  Is that what it is supposed to do?  I checked and it says that the artwork is installed?  I don't know what it is supposed to look like, so I guess it is right.  Maybe someone can comment on this?  Thanks.

Shane

---

### Post by knn on 2006-06-28
[QUOTE=shane2peru]Well, I take that back.  I get the Ubuntu when logging off and the Kubuntu when booting up.  Is that what it is supposed to do?  I checked and it says that the artwork is installed?  I don't know what it is supposed to look like, so I guess it is right.  Maybe someone can comment on this?  Thanks.

Shane[/QUOTE]

ok, open terminal and type
```
sudo update-initramfs -u
```
that should fix it (you should have ubuntu on bootup too)

---

### Post by jpmorelli on 2006-08-24
Yeah ! That's what I'm looking for !!! It works for me, with the two sudo commands works perfectly.
Thank's a lot, I do like the Brown Ubuntu.

---

