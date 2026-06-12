---
title: "Behind the scenecs in Evolution"
date: 2005-06-22
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-06-22
Does anyone know where Evolution keeps my calendars, address book and mail files? I'm looking but I'm not finding.

and the format for each? If I put icals there, or mab files or mbox (+msf?) files do they work? I know i can import them, but that's not much use for thunderbird on windows to keep updated. Hopefully i will be replacing evo's datastore files with symbolic links to thunderbird's own.

Cheers
Dave

---

### Post by mr_mop on 2005-06-22
from the console do a ls -a in your home directory (cd ~).  you'll see a directory called .evolution ( the . at the start means its hidden) all your data is in there.

---

