---
title: "Easy way to add device in fstab"
date: 2009-01-30
forum: General Help
---

### Post by Oldhacker on 2009-01-30
After making an error more than once when attempting to add a device to fstab, I thought of another way to assure that I was doing it without failure.

Manually add the device, and the correct line of parameters appears in mtab. Copy that line with an editor. Then, after making a backup copy of fstab to another name (for safety) open up fstab with an editor such as vi, and then type in the line that was copied from mtab. It worked perfectly for me.:D

Upon rebooting, the device was mounted.

---

### Post by dcstar on 2009-01-30
> **Oldhacker said:**
> After making an error more than once when attempting to add a device to fstab, I thought of another way to assure that I was doing it without failure.

Manually add the device, and the correct line of parameters appears in mtab. Copy that line with an editor. Then, after making a backup copy of fstab to another name (for safety) open up fstab with an editor such as vi, and then type in the line that was copied from mtab. It worked perfectly for me.:D

Upon rebooting, the device was mounted.

Or install the **pysdm** package and then use that - two steps instead of many.

---

### Post by Oldhacker on 2009-01-31
After installing pysdm, I tried to see what it does in a graphical format. The application came up either as sudo pysdm or from the Administration - Storage Device Manager menu.

Then, both of the general Configuration or Dynamic configuration rules tabs are just greyed out. :(

I don't need it now, but would like to know how to use it.

Thanks

---

