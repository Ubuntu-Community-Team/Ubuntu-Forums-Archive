---
title: "Help installing NWN + Expansions"
date: 2006-07-08
forum: Gaming &amp; Leisure
---

### Post by walkerx on 2006-07-08
I've followed the howto for [install instructions]("http://www.ubuntuforums.org/showthread.php?t=168331"), and downloaded the relevant files

_files downloaded_
hordes_of_the_underdark.run
nwn_129_final.run
nwn_129_english.run
shadows_of_undrentide.run
[U]
libgtk1.2[/U]
sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree... Done
libgtk1.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

As you can see I've already got libgtk installed

:~/nwninstaller$ ./nwn_129_final.run
Verifying archive integrity... All good.
Uncompressing Neverwinter Nights 1.29 for Linux...............................................................................
:~/nwninstaller$

it doesn't ask me for cd's or anything, so can't continue to step 3 in the howto

please can any one advise what maybe wrong

---

### Post by SpEcIeS on 2006-07-08
Try out this link. There maybe something for you there:

**[http://nwn.bioware.com/forums/viewforum.html?forum=72](http://nwn.bioware.com/forums/viewforum.html?forum=72)**

I have been using nwn on linux for quite some time, but I did not use the tutorial that you used. It is always better to apply the Bioware installation.

Remember to apply the 1.67 patch. :)

---

### Post by sidefx on 2006-07-08
What happens if you try "sudo ./nwn_129_final.run" ?

---

### Post by walkerx on 2006-07-08
Thanks Species,

I followed bioware's instructions and used my windows copy by mounting the drive and then copying it to linux partition, applied the patch - didn't need to do the fixinstall but tried it anyway and reported that patch.key was missing.

Not sure why but only got xp1patch.key and xp2patch.key, could be because i've got SoU and HoD and updated it to 1.67 already.

I even created a script linker to actually run it and it works fine, at moment just downloading the full 1gb linux resource for future reference.

thanks again for help

sidefx
i think I had tried that and it didn't work, in the end I followed instructions on bioware's webpage and its all working with my save games as well

only thing I'm back in luskan after losing a set off backups

---

### Post by Matrix101 on 2006-07-09
You should use the Installers form [http://www.liflg.org](http://www.liflg.org) ;)

---

### Post by walkerx on 2006-07-09
thanks Matrix,

this is output from that installer

Downloads$ sh nwn_1.29-multilanguage.run
Verifying archive integrity... All good.
Uncompressing Neverwinter Nights: 1.29-multilanguage Installer.....................................................................................................................................................................

Gdk-WARNING **: locale not supported by C library

but it continues

---

