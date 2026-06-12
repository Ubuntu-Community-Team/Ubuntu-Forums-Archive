---
title: "Boot Time Error"
date: 2009-04-13
forum: General Help
---

### Post by suresh_vandiyur on 2009-04-13
[B]kinit : name_to_dev_t (/dev/disk/by-uuid/f611a65c-5bda-40df-9ce2-c9e5dbbc1a85) = Sda3(8,3)
kinit : trying to resume from /dev/disk/by-uuid/f611a65c-5bda-40df-9ce2-c9e5dbbc1a85
kinit : No resume image, doing normal boot...[/B]**** the above error was occured whenever i start my system.. how to recover is problem... anyone know means reply me..

---

### Post by Aubergines on 2009-04-13
Is it actually causing booting problems? I could be wrong but as far as I can tell it's not an error, it just notifies that there's no suspend to disk image found and thus continuing with the normal boot process. Which is be fine, unless you shut down the machine by using the hibernate feature and it's not using restoring properly.

---

