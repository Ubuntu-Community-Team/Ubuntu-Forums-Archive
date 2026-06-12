---
title: "run custom script on gnome3 shutdown"
date: 2012-01-03
forum: Desktop Environments
---

### Post by RikoW on 2012-01-03
Dear all,

how do I execute a custom script when gnome3 shuts down either via logout or shutdown of the computer?

I always have VMware virtual machines running in the background. I want to suspend them automatically before the gnome session closes. So I somehow need to tab into the gnome shutdown sequence.

Thanks and cheers,
Riko

---

### Post by Bobhuber on 2012-01-03
> **RikoW said:**
> Dear all,

how do I execute a custom script when gnome3 shuts down either via logout or shutdown of the computer?

I always have VMware virtual machines running in the background. I want to suspend them automatically before the gnome session closes. So I somehow need to tab into the gnome shutdown sequence.

Thanks and cheers,
Riko
Use cairo-dock or screenlets and create a desktop launcher to execute your script with < sudo shutdown now> as the last command in the script

---

