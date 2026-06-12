---
title: "Upgraded to Catalyst 10.7 and no 3d effects anymore"
date: 2010-08-04
forum: Desktop Environments
---

### Post by erikla2002 on 2010-08-04
I have been happily running Ubuntu 10.04 64-bit for some time now with an ATI 4770 and Catalyst 10.1 drivers (I think). I read some about 10.7 and decided it was time to upgrade. I followed the instructions from ATI (sh ./ati-driver-installer-10-7-x86.x86_64.run). First time I didnt do sudo /usr/bin/aticonfig --initial

When I booted Compiz wasn't working anymore and Visual Effects under Appearance couldn't be enabled. I then uninstalled the 10.7 drivers (sudo sh ./fglrx-uninstall.sh) and installed the 10.1 again but it still doesn't work! What could be the probelm? I can't even open ATI Control Center anymore. The GUI never appears. 

I have tried to install the catalyst drivers several times and rebooted.

---

### Post by brokenromeo on 2010-08-04
A couple of questions, is your card supported by the 10.7 drivers, and did your uninstall succeed...did you get confirmation, I assume you ran the uninstall from the /usr/bin/aticonfig directory?

---

### Post by erikla2002 on 2010-08-04
> **brokenromeo said:**
> A couple of questions, is your card supported by the 10.7 drivers, and did your uninstall succeed...did you get confirmation, I assume you ran the uninstall from the /usr/bin/aticonfig directory? 

Yes my card is supported. Uninstall went fine and I was in /usr/share/ati. 

Output:
erikla@erikla-desktop:/usr/share/ati$ sudo sh ./fglrx-uninstall.sh
restore of system environment completed
Uninstall fglrx driver complete...
erikla@erikla-desktop:/usr/share/ati$ 


When I boot after that it says Ubuntu is running in low graphics mode so I assume the uninstall went fine. What I don't get is why the 3d effects etc won't work when I install the old version that worked before.

---

### Post by brokenromeo on 2010-08-04
Does fglrxinfo give you any info?

---

### Post by erikla2002 on 2010-08-05
> **brokenromeo said:**
> Does fglrxinfo give you any info?

erikla@erikla-desktop:~$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  157 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  18
  Current serial number in output stream:  18


I can now open ATI control center. See attached picture. Shouldn't it say something under OpenGL driver etc?



EDIT: It works now, I deleted /usr/share/ati and uninstalled fglrx via synaptic and reinstalled via synaptic.

---

### Post by hamidoo on 2010-08-15
ok what's the output of:
```

ldd `which fglrxinfo`

```

this line must be included in the output for proper functioanlity:
```

libGL.so.1 => /usr/lib/fglrx/libGL.so.1

```

---

