---
title: "Ignore broken dependencies for 1 specific package"
date: 2009-05-16
forum: General Help
---

### Post by zemon on 2009-05-16
Hello,

I installed an old version of rdiff-backup (because the current version won't talk to the backup server) and now the update-manager displays a warning sign. Can I tell the update-manager (apt-get?) to ignore the broken dependencies for just this one package?

Thanks,
-- Art Z.

---

### Post by 73ckn797 on 2009-05-16
> **zemon said:**
> Hello,

I installed an old version of rdiff-backup (because the current version won't talk to the backup server) and now the update-manager displays a warning sign. Can I tell the update-manager (apt-get?) to ignore the broken dependencies for just this one package?

Thanks,
-- Art Z.

The program "depends" on other parts so I do not see how it would work. Did you completely removed the other version prior to installing?

---

### Post by zemon on 2009-05-16
> **73ckn797 said:**
> The program "depends" on other parts so I do not see how it would work. Did you completely removed the other version prior to installing?

I did edit the first line of the executable, changing "#!/usr/bin/python" to "#!/usr/bin/python2.5" but other than that, it works great. I just need to turn off the warning.

If there isn't a way to turn off the warning then I guess I need to delete the package and install from source.

-- Art Z.

---

