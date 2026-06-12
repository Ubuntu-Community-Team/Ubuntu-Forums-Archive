---
title: "Ubuntu 16.04 won't boot - ERST error"
date: 2018-01-04
forum: Desktop Environments
---

### Post by petew1 on 2018-01-04
So I have a HP Microserver which was running 14.X Ubuntu for ages. Due to adding a new disk and a lack of space in root on the system, I decided to re-install from scratch using 16.04. 
Kernel currently is 4.10.0-42-generic  That was successful. But since then, 9 times of 10 the system does not boot. 
I get these errors 
"ERST: failed to get log address" in log message.
  "BERT: Can't request iomem region 0000000077fab650-0000000077fab6aa3"
 "ata2.00: failed to enable AA"  I've no idea what those mean. It then enters "emergency mode" 

A bit of googling suggested a BIOS update to the Microserver which I did. Hasn't helped. I can usually get the system to boot with a combination of rebooting (multiple times) and/or power on/off. But this is not really acceptable for a reliable server.  I don't think the issue is related to the new HDD (which is not the boot disk) as if I remove it, I still have the same issue.

  Anyone able to point me to what these errors mean and how to fix the issue? I'm considering downgrading back to 14.X  Thanks

---

