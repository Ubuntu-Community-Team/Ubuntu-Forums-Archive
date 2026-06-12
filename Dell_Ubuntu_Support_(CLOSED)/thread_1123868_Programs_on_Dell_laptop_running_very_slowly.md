---
title: "Programs on Dell laptop running very slowly"
date: 2009-04-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by islandrailsgeek on 2009-04-12
Hello,
  I have a Dell Inspiron 1525. I'm running Ubuntu 8.10. When I boot it up and start program, the programs take a really long time to launch and once they launch they are totally unresponsive. 

I suspect this is some type of hardware issue, perhaps related to the hard drive. When I do a top, I do not see anything sucking up all the CPU cycles.
 If anyone can help me diagnose the problem, I would really appreciate it. The laptop is still under the 1 year warranty. This is what I find in my /var/log/messages:

pr 12 07:32:54 lighthouse kernel: [49931.799019] Descriptor sense data with sense descriptors (in hex):
Apr 12 07:32:54 lighthouse kernel: [49931.799025]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 12 07:32:54 lighthouse kernel: [49931.799052]         0a 71 0c d1 
Apr 12 07:32:54 lighthouse kernel: [49931.799063] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Apr 12 07:32:54 lighthouse kernel: [49931.799109] ata3: EH complete
Apr 12 07:32:54 lighthouse kernel: [49931.799228] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Apr 12 07:32:54 lighthouse kernel: [49931.799272] sd 2:0:0:0: [sda] Write Protect is off
Apr 12 07:32:54 lighthouse kernel: [49931.799347] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 12 07:32:54 lighthouse kernel: [49936.072519] ata3.00: configured for UDMA/133
Apr 12 07:32:54 lighthouse kernel: [49936.072555] ata3: EH complete
Apr 12 07:32:54 lighthouse kernel: [49936.072709] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Apr 12 07:32:54 lighthouse kernel: [49936.072751] sd 2:0:0:0: [sda] Write Protect is off
Apr 12 07:32:54 lighthouse kernel: [49936.072821] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 12 07:32:54 lighthouse kernel: [49940.089065] ata3.00: configured for UDMA/133
Apr 12 07:32:54 lighthouse kernel: [49940.089092] ata3: EH complete
Apr 12 07:32:54 lighthouse kernel: [49940.089197] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Apr 12 07:32:54 lighthouse kernel: [49940.089238] sd 2:0:0:0: [sda] Write Protect is off
Apr 12 07:32:54 lighthouse kernel: [49940.089313] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 12 07:32:54 lighthouse kernel: [49944.215817] ata3.00: configured for UDMA/133
Apr 12 07:32:54 lighthouse kernel: [49944.215844] ata3: EH complete
Apr 12 07:32:54 lighthouse kernel: [49944.215985] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Apr 12 07:32:54 lighthouse kernel: [49944.216054] sd 2:0:0:0: [sda] Write Protect is off
Apr 12 07:32:54 lighthouse kernel: [49944.216132] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 12 07:32:54 lighthouse kernel: [49948.211271] ata3.00: configured for UDMA/133
Apr 12 07:32:54 lighthouse kernel: [49948.211297] ata3: EH complete
Apr 12 07:32:54 lighthouse kernel: [49948.211437] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Apr 12 07:32:54 lighthouse kernel: [49948.211482] sd 2:0:0:0: [sda] Write Protect is off
Apr 12 07:32:54 lighthouse kernel: [49948.211558] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 12 07:32:54 lighthouse kernel: [49952.505910] ata3.00: configured for UDMA/133
Apr 12 07:32:54 lighthouse kernel: [49952.505940] ata3: EH complete
Apr 12 07:32:54 lighthouse kernel: [49952.506049] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Apr 12 07:32:54 lighthouse kernel: [49952.506092] sd 2:0:0:0: [sda] Write Protect is off
Apr 12 07:32:54 lighthouse kernel: [49952.506166] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 12 07:32:54 lighthouse kernel: [49956.510269] ata3.00: configured for UDMA/133
Apr 12 07:32:54 lighthouse kernel: [49956.510305] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr 12 07:32:54 lighthouse kernel: [49956.510315] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 12 07:32:54 lighthouse kernel: [49956.510329] Descriptor sense data with sense descriptors (in hex):
Apr 12 07:32:54 lighthouse kernel: [49956.510338]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 12 07:32:54 lighthouse kernel: [49956.510368]         0a 71 0c d1 
Apr 12 07:32:54 lighthouse kernel: [49956.510381] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Apr 12 07:32:54 lighthouse kernel: [49956.510425] ata3: EH complete
Apr 12 07:32:54 lighthouse kernel: [49956.510521] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Apr 12 07:32:54 lighthouse kernel: [49956.510561] sd 2:0:0:0: [sda] Write Protect is off
Apr 12 07:32:54 lighthouse kernel: [49956.510632] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA


Could this be a harddrive problem?

Kevin

---

### Post by Temposs on 2009-04-13
Try booting into recovery mode and running fsck, which will scan your harddrive for problems, and try to fix them. It could be a harddrive problem.

---

