---
title: "WD My passport...."
date: 2009-02-07
forum: General Help
---

### Post by SunnyRabbiera on 2009-02-07
Alright SERIOUS issue here!
My WD external will no longer mount!
It has worked before but now refuses to come up!
And when it did mount it would only stay mounted for a VERY short time, it would only mount for 3 minutes then un mount for no reason whatsoever...
I cant take it back, warranty is gone and well I hope that $80 of my much needed money isnt wasted here...
HELP!!!!!

---

### Post by cariboo on 2009-02-07
What is the output of dmesg when you plug your device in and then when it disconnects? In a Applications-->Accessories-->Terminal type:

```
dmesg | tail -n20
```

the above command will print out the last 20 lines of dmesg. The output should tell you what is happening.

Jim

---

### Post by SunnyRabbiera on 2009-02-07
```
dmesg | tail -n20
[  850.931342] sd 5:0:0:0: Attached scsi generic sg3 type 0
[  917.184856] usb 5-6: USB disconnect, address 5
[  984.849030] usb 5-6: new high speed USB device using ehci_hcd and address 6
[  984.991382] usb 5-6: configuration #1 chosen from 1 choice
[  985.068534] scsi6 : SCSI emulation for USB Mass Storage devices
[  985.103297] usb-storage: device found at 6
[  985.103310] usb-storage: waiting for device to settle before scanning
[  990.102318] usb-storage: device scan complete
[  990.121050] scsi 6:0:0:0: Direct-Access     WD       2500BEV External 1.75 PQ: 0 ANSI: 4
[  990.124018] sd 6:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[  990.125146] sd 6:0:0:0: [sdb] Write Protect is off
[  990.125157] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  990.125162] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  990.127013] sd 6:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[  990.128010] sd 6:0:0:0: [sdb] Write Protect is off
[  990.128020] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  990.128025] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  990.128963]  sdb: sdb1
[  990.176363] sd 6:0:0:0: [sdb] Attached SCSI disk
[  990.177795] sd 6:0:0:0: Attached scsi generic sg3 type 0
```

Okay now what?

---

### Post by SunnyRabbiera on 2009-02-07
Hello?
I really need this fixed!

---

### Post by SunnyRabbiera on 2009-02-07
Bump

---

### Post by SunnyRabbiera on 2009-02-07
HELLO!
Am I speaking to thin air here!

---

### Post by SunnyRabbiera on 2009-02-24
alright seriously I need help here, what do I have to do speak latin?????

---

### Post by Slim Odds on 2009-02-24
> **SunnyRabbiera said:**
> alright seriously I need help here, what do I have to do speak latin?????

You can nag all you want, but in a **free** support forum, you get what you get.

I wish I could help you.

Is there no indication in your logs what might have happened?

---

### Post by SunnyRabbiera on 2009-02-24
I dont have any logs that say error...
I just think its busted, well there goes $80 down the @#$^ tubes.
GAH!
I guess I wont buy WD again, seagate here I come.

---

