---
title: "Having a problem with digital camera now..."
date: 2006-10-02
forum: Desktop Environments
---

### Post by someguyouknow on 2006-10-02
before today, i could easily plug in the cam and the window will pop up with the folders so i could transfer them...
now, i get an error that says "An unknown error has occurred"

i am not sure what to do about that...

thanks in advance...

---

### Post by Jussi Kukkonen on 2006-10-02
That error message is not too informative... do a 
```
tail -fn 0 /var/log/messages
```
then plug the camera in, and paste the output here.

---

### Post by someguyouknow on 2006-10-02
```
Oct  2 09:19:59 localhost kernel: [17221357.468000] ohci_hcd 0000:00:0b.0: wakeu               p
Oct  2 09:20:00 localhost kernel: [17221357.852000] usb 1-7: new full speed USB                device using ohci_hcd and address 20
Oct  2 09:20:00 localhost kernel: [17221358.068000] scsi20 : SCSI emulation for                USB Mass Storage devices
Oct  2 09:20:05 localhost kernel: [17221363.076000]   Vendor: HP        Model: U               SB CAMERA        Rev: 1.00
Oct  2 09:20:05 localhost kernel: [17221363.076000]   Type:   Direct-Access                                     ANSI SCSI revision: 00
Oct  2 09:20:05 localhost kernel: [17221363.084000] SCSI device sdb: 31201 512-b               yte hdwr sectors (16 MB)
Oct  2 09:20:05 localhost kernel: [17221363.092000] sdb: Write Protect is off
Oct  2 09:20:05 localhost kernel: [17221363.120000] SCSI device sdb: 31201 512-b               yte hdwr sectors (16 MB)
Oct  2 09:20:05 localhost kernel: [17221363.124000] sdb: Write Protect is off
Oct  2 09:20:05 localhost kernel: [17221363.124000]  sdb: sdb1
Oct  2 09:20:05 localhost kernel: [17221363.172000] sd 20:0:0:0: Attached scsi r               emovable disk sdb
Oct  2 09:20:05 localhost kernel: [17221363.172000] sd 20:0:0:0: Attached scsi g               eneric sg0 type 0
Oct  2 09:20:06 localhost kernel: [17221364.376000] printk: 10 messages suppress               ed.

```

---

### Post by Jussi Kukkonen on 2006-10-02
Hmm... Nothing supicious there. 

Is there any indication on the error message on what application it belongs to? I'm guessing it's gthumb, but I am not really an expert on this...

---

