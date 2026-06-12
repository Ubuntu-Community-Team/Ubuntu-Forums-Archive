---
title: "udf optical drive not working in nautilus"
date: 2007-05-21
forum: Desktop Environments
---

### Post by StolenNomenclature on 2007-05-21
Using Ubuntu 7.04 x64 I have inserted a rewriteable DVD into the drive that is formatted with UDF, and attempt to copy some files to it via drag-and-drop within Nautilus. One of more files may copy, but eventually an error message about the disk possibly being full will come up and only some of the files will have copied. From now on it is impossible to copy additional files, or even properly delete files already there.

Doing the same thing after a fresh install of Kubuntu 7.04 x64, this time  using Konqeror (KDE) works fine. The files copy without error and I can perform any number of additoional copies and deletes and it all works.

The above also works if I first install Ubuntu and then apt-get to add KDE rather than doing a fresh install of Kubuntu.

But the most interesting thing is that after adding KDE using apt-get to Ubuntu, I can now copy files using Nautilus, which formerly did not work. Adding KDE somehow fixes Gnome.

I note that the package "pmount" is used by Kubuntu and not by Ubuntu, but if KDE is added to Ubuntu via apt-get, the pmount package is added also. Perhaps its this package which also makes Gnome work by doing a proper automount of the optical disk. Gnome seems to use the package "gnome-mount" but it would seem that oince KDe is added pmount maybe takes precedence.

Anyone have any idea what is going on here?

Thanks,;)

---

