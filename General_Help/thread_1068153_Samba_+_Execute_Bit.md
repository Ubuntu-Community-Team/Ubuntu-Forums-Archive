---
title: "Samba + Execute Bit"
date: 2009-02-12
forum: General Help
---

### Post by Stevai on 2009-02-12
Forgive me if this has been answered previously (sure it has, I just haven't been able to find it) ...

I have a Maxtor Central Axis NAS drive (I suggest against anyone buying one) that runs a closed access variant of Linux. I am aware there are modified upgrades that allow for SSH access, but, I'd prefer to stick with factory upgrades at this point.

This drive only allows for a Samba connection for file sharing. So, is it possible to setup Samba so that the execute bit is maintained correctly when working on a file in Linux, then Windows since Samba maps the execute bits to the Windows-specific archive/system file attributes? If so, how? I'd need it to be recursive on a mount point.

---

### Post by lykwydchykyn on 2009-02-12
I believe the correct config file directives are:
```

map system = no
map archive= no
map hidden = no

```

I know you can put that globally (under the [global] section of smb.conf), but I don't know about per-share.

---

### Post by Stevai on 2009-02-17
> **lykwydchykyn said:**
> I believe the correct config file directives are:
```

map system = no
map archive= no
map hidden = no

```

I know you can put that globally (under the [global] section of smb.conf), but I don't know about per-share.

I could've sworn I tried this, but will give it a go when I get onto the Linux box shortly ... who knows, tried so many different things.

---

