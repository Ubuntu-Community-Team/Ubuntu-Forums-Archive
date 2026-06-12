---
title: "Vostro 1500 DVD drive firmware update"
date: 2007-12-26
forum: Dell  Ubuntu Support
---

### Post by peterff on 2007-12-26
Has anyone installed Dell's firmware update for the Vostro 1500's Hitachi DVD drive? I've got two qualms about it: First, Dell says that it's only compatible with Windows. I suspect this may mean that the installation utility only works in Windows, and the drive would still function in Linux after the update. Second, the Dell page describes the drive as HLDS GSA-T21N, but 'dmesg | grep DVD' gives me the following output:

[    4.620000] ata1.00: ATAPI: HL-DT-ST DVD+/-RW GSA-T11N, A103, max UDMA/33
[    4.796000] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-T11N A103 PQ: 0 ANSI: 5

As you can see, the drive is described there as a GSA-T11N. The Dell update is listed under the Vostro 1500, however, so I'm confused as to whether this is actually my drive.

---

### Post by XP-FREAK on 2007-12-26
I didn't install it yet, but do you know which advantages this firmware upgrade brings along?

---

### Post by peterff on 2007-12-26
Dell says "This will improve the level of acoustic noise and vibration of the optical drive." They also say its purpose is to "To improve the customer experience for listening to audio CD." I was interested because my drive makes a lot of noise sometimes.

---

### Post by XP-FREAK on 2007-12-27
Woa, this sounds really usefull because the DVD drive makes really a lot of noise. For me, it shouldn't be a problem to install this. I still have Vista on my Vostro!

---

### Post by peterff on 2007-12-27
Yeah, I've still got Vista on mine as well. If you do install it, could you tell me if it works? And could you let me know whether 'dmesg | grep DVD' shows the same drive as mine?

---

### Post by XP-FREAK on 2007-12-30
OK, my vostro has a HL-DT-ST DVD+-RW GSA-T11N ATA Device

Dell shows 3 firmware updates, but no one seems to fit for this device.
Looks like i've to wait and listen to the cute noise of my dvd drive :(

---

