---
title: "How to reinstall KDE 4?"
date: 2009-11-15
forum: Desktop Environments
---

### Post by kajman on 2009-11-15
I have a problem with missing icons under KDE4. I've searched the forums, and someone told that reinstalling KDE4 helped him. How can I do this myself?

---

### Post by SuperSonic4 on 2009-11-15
The easiest way would be to reinstall whichever distro you had with kde on.

You may be able to force the installation of *kubuntu-desktop* in apt. Have you thought about changing the icon theme first?

---

### Post by kajman on 2009-11-15
Yes, I've tried, but the same icons are still missing.

It is seen especially in Krusader, I attach an screenshot.

Also I think this is not a Krusader problem only, (there's a icon missing in Kate also, and seen some others missing somewhere). I've deleted Krusader config, and it still didn't have any icons.

I don't want to reinstall whole distro, because it is always much work with it, and I don't have much time for it now.

---

### Post by Zorael on 2009-11-15
Hmm, would that be the kde-icons-oxygen package?
```
$ sudo aptitude reinstall kde-icons-oxygen
```

---

### Post by kajman on 2009-11-15
Tried to reinstall it already through synaptic. Reinstalled now as you have said. Didn't help also.

---

### Post by Zorael on 2009-11-15
If you create a new user, do icons work properly when logged in as him/her/it?

Looking through the icons (in /usr/share/icons/oxygen), practically all are from kde-icons-oxygen. The only thing I can think of is that you have an overriding user-specific icon theme being used, in which case the icons would show normally for another user.

---

### Post by kajman on 2009-11-15
I've created a new user, and here's the screen for Krusader first-time configuration screen. Icons are still obviously missing.

---

### Post by Zorael on 2009-11-16
Curious.

I don't use Krusader, but I installed it and had a look. It seems like the icons which show in your picture as missing are non-Oxygen icons. They look like the KDE3 Crystal theme.

```
$ sudo aptitude reinstall kdelibs-data
```
If the next command doesn't output crystalsvg, that might be a cause, too.
```
$ file /usr/share/icons/default.kde
/usr/share/icons/default.kde: symbolic link to `crystalsvg'
```

---

### Post by kajman on 2009-11-16
I did as you said, and reinstalled kdelibs-data and rebooted the system.

Also the output of that command is just as you said it should be:
```
 $ file /usr/share/icons/default.kde
/usr/share/icons/default.kde: symbolic link to `crystalsvg'
```

Needless to say, it didn't help. Maybe my icons are cursed, not just missing :P

---

### Post by Zorael on 2009-11-22
You could ask in #kde on irc.freenode.net; hopefully someone there knows more about the intrinsic details of where KDE looks to find icons, and what might cause it to fail.

---

