---
title: "pysdm"
date: 2008-12-30
forum: General Help
---

### Post by Totenglocke on 2008-12-30
I was looking for an easy way to auto mount a partition and I found pysdm.  Now that it's installed I can't mount my partition unless I open up pysdm and click 'mount' since it says I no longer have permission (always had permission before) and resetting everything to defaults and removing pysdm doesn't fix the problem.  Any ideas?

---

### Post by maddog46113 on 2008-12-30
Make sure your starting pysdm as root 

```
sudo pysdm
```

Click on the hard drive you want to auto mount. Click assistant.
check the box that says this file system is mounted at boot time.

---

### Post by dcstar on 2008-12-30
> **maddog46113 said:**
> Make sure your starting pysdm as root 

```
sudo pysdm
```

Click on the hard drive you want to auto mount. Click assistant.
check the box that says this file system is mounted at boot time.

Using the installed launcher - System-Administration-Storage Device Manager - always starts it with gksudo (as it should be).

It should NEVER be run on its own as a user.

---

### Post by Totenglocke on 2008-12-30
The main problem with pysdm is that I dual boot (hence wanting to mount the other parition) and my folders for my mail in Thunderbird are stored on that partition -- due to pysdm messing with permissions, I can no longer open those folders even once the partition is mounted.  So now I can no longer access my old emails in Ubuntu.

---

### Post by dcstar on 2008-12-30
> **Totenglocke said:**
> The main problem with pysdm is that I dual boot (hence wanting to mount the other parition) and my folders for my mail in Thunderbird are stored on that partition -- due to pysdm messing with permissions, I can no longer open those folders even once the partition is mounted.  So now I can no longer access my old emails in Ubuntu.

pysdm allows you to set/change whatever permissions you want on the mount point, all it does it set some defaults and if you don't bother to change them then that is what is used.

---

