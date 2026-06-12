---
title: "file roller and un-RARing"
date: 2005-03-24
forum: Desktop Environments
---

### Post by Steel3 on 2005-03-24
Hey all,

After recently trying to uncompress a .rar archive, I came to the realization that in Hoary decompressing RAR archives is no longer a built-in feature into the file-roller program (taking a quick look at the list it seemed as though it supported far fewer options now).  I installed the unrar package, but still was not able to uncompress an archive I could decompress in Warty.  Any idea on how to get back this capability, and why it was taken out?

Thanks

---

### Post by lao_V on 2005-03-24
It seems that there are lot of service menus that have not been inlcluded in Kubuntu at the moment. However, you can download the ones you like from [here.]("http://www.kde-apps.org/content/show.php?content=13544")
Hope they inlclude them in the release version of kubuntu

---

### Post by Poldi on 2005-03-24
neither the free nor the unfree 'unrar' package from the repository works. the shareware 'rar' package does, though. it seems the file-roller can only work with a "rar -E file´name.rar" internally.

---

### Post by Steel3 on 2005-03-24
[QUOTE=lao_V]It seems that there are lot of service menus that have not been inlcluded in Kubuntu at the moment. However, you can download the ones you like from [here.]("http://www.kde-apps.org/content/show.php?content=13544")
Hope they inlclude them in the release version of kubuntu[/QUOTE]

Hmm, I followed all of the directions and tried the "extract to subdirectory" action and it still didn't work.  As the previous poster mentioned, it seems like its a problem with the package that the system chooses to use to extract stuff.  Really hope they rectify this for the final release -- in the meantime, I'll probably just install the .deb

---

### Post by lao_V on 2005-03-24
[QUOTE=Nirmal Mankani]Hmm, I followed all of the directions and tried the "extract to subdirectory" action and it still didn't work.  As the previous poster mentioned, it seems like its a problem with the package that the system chooses to use to extract stuff.  Really hope they rectify this for the final release -- in the meantime, I'll probably just install the .deb[/QUOTE]
 Have you looked at the file extensions in kcontrol to check which app handles rar files?

---

### Post by Steel3 on 2005-03-24
[QUOTE=lao_V]Have you looked at the file extensions in kcontrol to check which app handles rar files?[/QUOTE]

Nope :-P

Before I got a chance to read this, I downloaded the deb [here](http://ftp.us.debian.org/debian/pool/non-free/r/rar/rar_3.30-2_i386.deb), and then everything seems to work out.  apt-get says that rar is referenced by other packages in the repository, but that it doesn't exist.  Most likely they took it out because it was non-free... definately hope they rectify this in the final release.

---

### Post by arazaxirelcinellersadolur on 2005-11-30
hi,
visit :

[http://www.ubuntuforums.org/showthread.php?t=56183](http://www.ubuntuforums.org/showthread.php?t=56183)

best regards,

---

