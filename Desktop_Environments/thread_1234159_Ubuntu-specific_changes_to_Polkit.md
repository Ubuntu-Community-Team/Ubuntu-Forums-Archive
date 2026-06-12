---
title: "Ubuntu-specific changes to Polkit"
date: 2009-08-07
forum: Desktop Environments
---

### Post by thermafrost on 2009-08-07
I need help in Ubuntufying the Debian installation on one computer. Converting to an outright Ubuntu install isn't an option for this computer at the moment (ext4 issues), but I would like my desktop experience to be as close as possible to Ubuntu, particularly with regard to the "locked" root account (sudo administrative-program).
My problem: in Debian I can't get polkit-gnome-authorization (menu: System/Administration/Authorizations) to work for the designated administrative user (the one blessed with sudo root rights). I need to supply a root password. Therefore I cannot use programs which demand the use of Polkit (rather than the simpler gksu framework).
Does anybody know what Ubuntu-specific chages to Polkit enables non-root users to modify Polkit authorizations?

---

