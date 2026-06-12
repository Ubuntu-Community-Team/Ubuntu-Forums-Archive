---
title: "[SOLVED] Kernel update breaks sound on dell 1525"
date: 2008-05-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by scooternew on 2008-05-26
I just did an update to Kernel 2.6.24-17-generic. and now hardy will not detect my sound card. I ran a depmod -a and regenerated the initramfs but still will not see the sound card. so i switched back to 2.6.24.16 and sound works perfectly using the old kernel. Any ideas??

Scott

---

### Post by scooternew on 2008-05-26
It's fixed now. i was following the instructions in dell [link]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade") and didn't realize i was still working on the -16 kernel instead of the new -17. sound working normally again.:)

---

