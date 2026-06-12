---
title: "suspend in ibook and sony vaio"
date: 2006-06-09
forum: Desktop Environments
---

### Post by murataht on 2006-06-09
I tried the suspend in sony vaio, and it worked, but takes too much time(one minute to wake up, but fast to suspend). 
with ibook g3, the suspend worked very fast(both suspend and wake up is fast). 

i don't know why there is a big difference in wake up time between linux for ppc and 686?

do you think if I compile my own kernel with the specific modules included in the kernel will help speed up the vaio wake up time? or is there other ways to speed it up? ...

thanks in advance. and any suggestion will do.

---

### Post by murataht on 2006-06-12
sorry for asking again, but does anybody know this???

---

### Post by btlee on 2006-06-12
[QUOTE=murataht]I tried the suspend in sony vaio, and it worked, but takes too much time(one minute to wake up, but fast to suspend). 
with ibook g3, the suspend worked very fast(both suspend and wake up is fast). 

i don't know why there is a big difference in wake up time between linux for ppc and 686?

do you think if I compile my own kernel with the specific modules included in the kernel will help speed up the vaio wake up time? or is there other ways to speed it up? ...

thanks in advance. and any suggestion will do.[/QUOTE]

ppc and 686 has very different architecture.
ppc uses pmu and apm emulation, but 686 uses usually apm or acpi for power management. But acpi firmware sometimes is very buggy.
I susect that you vaio does not suspend to ram, but suspend to disk.
If it is true, your slow wake-up is normal.

---

### Post by murataht on 2006-06-13
thanks for the replay. 
if it is suspending to the disk, how can I configure it to suspend to ram?
will it be faster? ...

thanks

---

### Post by murataht on 2006-06-13
no suggestions???

---

### Post by patrickfromspain on 2006-06-13
Maybe you can have a look into /etc/default/acpi-support. There you can see if you have both sleep (suspend to ram) and hibernate (suspend into hdd) enabled.

---

### Post by murataht on 2006-06-15
from /etc/defaults/acpi-support, it is obvious that i am using suspend to ram. thanks.
but still there is no source to speed up this "wake up" process. Is there any source that i could consult??? thanks!!!

---

