---
title: "Difference between kubuntu-desktop and kde metapackages"
date: 2005-05-23
forum: Desktop Environments
---

### Post by davide_bruzzone on 2005-05-23
Greetings all...

I just got done installing Ubuntu 5.04 on my laptop last night and would like to install KDE (I'm both a Gnome and KDE user, but prefer KDE).

According to the KDE installation documentation in the UserDocumentation portion of the wiki, the kubuntu-desktop metapackage is "recommended". Beyond that, there's no information about the differences between the kubuntu-desktop and kde metapackages (beyond the information available on packages.ubuntu.com or via Synaptics).

What I'd like to do is install and be able to use KDE without blowing away Gnome (and would, if possible, like to choose one of the two when I log in). I also need to install KDevelop.

Can anyone who has installed either metapackege please let me know what the major differences between the two are (and what tweaks the kubuntu-default-settings package contains)?

Cheers...

Davide Bruzzone

---

### Post by elsewhere on 2005-05-23
I believe (and someone please correct me if I'm wrong) that the KDE metapackage will give you a "vanilla" KDE installation, whereas the kubuntu metapackages give you the default settings such as the wallpaper, splash screen etc.  Functionality should be the same.  You will have to add in KDevelop separately but you should be able to select it at the same time in synaptic.

There's no conflict with kubuntu-desktop and gnome, except that kubuntu will install KDM which will cause a conflict with GDM, and X will force you to choose one (same thing happens when installing ubuntu-desktop into a kubuntu installation).

Hope this helps...

Cheers,
KV

---

### Post by davide_bruzzone on 2005-05-23
[QUOTE=elsewhere]I believe (and someone please correct me if I'm wrong) that the KDE metapackage will give you a "vanilla" KDE installation, whereas the kubuntu metapackages give you the default settings such as the wallpaper, splash screen etc.  Functionality should be the same.  You will have to add in KDevelop separately but you should be able to select it at the same time in synaptic.

There's no conflict with kubuntu-desktop and gnome, except that kubuntu will install KDM which will cause a conflict with GDM, and X will force you to choose one (same thing happens when installing ubuntu-desktop into a kubuntu installation).

Hope this helps...

Cheers,
KV[/QUOTE]

KV,

Thanks for the response! It definately helps! I think I'll try the recommended approach (i.e. The kubuntu-desktop metapackage) and will install KDevelop separately (Unlike kubuntu-desktop, the kde metapackage includes KDevelop)...

Cheers...

Davide Bruzzone

---

