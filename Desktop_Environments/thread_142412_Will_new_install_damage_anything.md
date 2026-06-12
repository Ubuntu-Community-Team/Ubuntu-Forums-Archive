---
title: "Will new install damage anything?"
date: 2006-03-10
forum: Desktop Environments
---

### Post by rogdef on 2006-03-10
When I upgrade Breezy to Dapper (?) will I need to do a new install and overwrite the old one? If so, will it delete any applications I have installed? What's the best way to upgrade releases? Thank you.

---

### Post by MichaelZ on 2006-03-10
Hello,

You can have a look at this link:

[http://www.macewan.org/2006/02/23/upgrading-breezy-to-dapper/](http://www.macewan.org/2006/02/23/upgrading-breezy-to-dapper/)

Best wishes,
Michael

---

### Post by Ubuntuud on 2006-03-10
When you have just one partition, the install of Dapper will overwrite _everything_. But if you have a seperate /home partition it is possible to choose not to overwrite that one, applications you installed in that directory will be "saved" all the others deleted.

---

### Post by lamego on 2006-03-10
It will NOT overwrite everything, it will only overwrite/remote the software for which new packages are available, other software (manually installed) and your home directories will not be removed. Please note that I am refering to upgrade (which is done with apt-get dist-upgrade).

---

### Post by rogdef on 2006-03-10
[QUOTE=lamego]It will NOT overwrite everything, it will only overwrite/remote the software for which new packages are available, other software (manually installed) and your home directories will not be removed. Please note that I am refering to upgrade (which is done with apt-get dist-upgrade).[/QUOTE]

So apt-get dist-upgrade will update to Dapper when it is available? Is it that easy?

---

