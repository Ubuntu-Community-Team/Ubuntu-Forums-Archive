---
title: "ALSA and Kernel Symble Mismatch"
date: 2008-02-14
forum: Desktop Environments
---

### Post by petersra on 2008-02-14
I have a gusty release along with the ALSA sound CA0106 drivers.  All works well until I get an ubuntu update with new kernel headers.  After that, the sound will not work.  The dmesg gives errors like:

nd_seq_dummy: disagrees about version of symbol snd_seq_kernel_client_dispatch
[   30.362790] snd_seq_dummy: Unknown symbol snd_seq_kernel_client_dispatch
[   30.362874] snd_seq_dummy: disagrees about version of symbol snd_seq_create_kernel_client
[   30.362876] snd_seq_dummy: Unknown symbol snd_seq_create_kernel_client
[   30.451855] usb 3-2: configuration #1 chosen from 1 choice
[   30.550235] snd_ac97_codec: disagrees about version of symbol snd_info_register

Each time I have to re-compile to get the sound working.  What am I doing wrong?

Thanks

---

