---
title: "OpenOffice 3.0.1 - cleanup needed"
date: 2010-01-04
forum: Desktop Environments
---

### Post by oygle on 2010-01-04
Have recently run the program 'fdupes' , to find duplicate files, and it picked up a lot of Openoffice files, such as ..

> 
~/.openoffice.org2/user/database/biblio/biblio.dbt
~/.openoffice.org/3/user/database/biblio/biblio.dbt

~/.openoffice.org2/user/database/biblio.odb
~/.openoffice.org/3/user/database/biblio.odb

~/.openoffice.org2/user/database/evolocal.odb
~/.openoffice.org/3/user/database/evolocal.odb

~/.openoffice.org2/user/config/autotbl.fmt
~/.openoffice.org/3/user/config/autotbl.fmt

~/.openoffice.org2/user/config/arrowhd_en-US.soe
~/.openoffice.org/3/user/config/arrowhd_en-US.soe

~/.openoffice.org2/user/config/styles_en-US.sod
~/.openoffice.org/3/user/config/styles_en-US.sod

~/.openoffice.org2/user/config/classic_en-US.sog
~/.openoffice.org/3/user/config/classic_en-US.sog

~/.openoffice.org2/user/config/palette_en-US.soc
~/.openoffice.org/3/user/config/palette_en-US.soc

~/.openoffice.org2/user/config/modern_en-US.sog
~/.openoffice.org/3/user/config/modern_en-US.sog

~/.openoffice.org2/user/config/soffice.cfg/global/accelerator/en-US/current.xml
~/.openoffice.org/3/user/config/soffice.cfg/global/accelerator/en-US/current.xml

~/.openoffice.org2/user/config/hatching_en-US.soh
~/.openoffice.org/3/user/config/hatching_en-US.soh


Obviously, in the upgrade from OpenOffice 2 ==> 3 , there wasn't a cleanup done. Who needs to be contacted to fix this please ?

Oygle

---

### Post by mörgæs on 2010-01-04
If you are sure that it is not a feature (the option to roll back to Open Office 2, for example), you can report it here:

[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

---

### Post by Hagar Delest on 2010-01-04
It **is** a feature! Each major branch uses its own profile to allow user to use both versions. Since they are major changes, first the old configuration files are not directly compatible (the 3.x welcome process can transfer the personal data, i.e. the old profile, but it's not that robust). Second, it's safer to avoid mixing 2 versions on the same profile.

If you don't use 2.x anymore, just delete the 2.x profile.

NB: now the branch number is under a main folder to avoid having several openoffice.org folders.

---

### Post by oygle on 2010-01-05
> **Hagar de l'Est said:**
> Each major branch uses its own profile to allow user to use both versions. Since they are major changes, first the old configuration files are not directly compatible (the 3.x welcome process can transfer the personal data, i.e. the old profile, but it's not that robust). Second, it's safer to avoid mixing 2 versions on the same profile.

I don't use profiles at all under OpenOffice. Had a bit of a look under 'options', and a few options had paths pointing to the 3.x path.

> **Hagar de l'Est said:**
> 
If you don't use 2.x anymore, just delete the 2.x profile.

Thanks, I will do that, as I only use 3.x

Oygle

---

### Post by Hagar Delest on 2010-01-05
> **oygle said:**
> I don't use profiles at all under OpenOffice.
The profile is created by OOo and it must be there to run. It is used to store all the configuration parameters related to the user (toolbars customization, wordbooks (added entries in the spell checker), macros, extensions, ...

---

