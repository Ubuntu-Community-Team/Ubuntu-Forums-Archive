---
title: "UUID number?"
date: 2009-05-06
forum: General Help
---

### Post by celticbhoy on 2009-05-06
How do I find the UUID number for an installed kernel ???

---

### Post by tarps87 on 2009-05-06
I believe UUID's are only used for identifying drives/ media stores.
To find out the UUID for a drive
```
sudo blkid
```
or
```
sudo vol_id -u /dev/*driveName*
```

If you are talking about editing the grubs' menu list you will want the UUID of the / drive

---

### Post by dabl on 2009-05-06
You don't.

UUI_D_ is a _device_ number -- for storage devices.

If you need the version number of your running kernel, the command is ```
uname -r
```

:)

---

### Post by whoop on 2009-05-06
Do you mean the uuid for your partition? If yes:

```

sudo blkid

```

---

### Post by tarps87 on 2009-05-06
> **dabl said:**
> You don't.

UUI_D_ is a _device_ number -- for storage devices.

If you need the version number of your running kernel, the command is ```
uname -r
```

:)

UUID's (Universally Unique Identifier) can be used for other things as it is just a unique identifier, although in Ubuntu I believe it is only used to identify storage devices.

---

