---
title: "Hard drive logging (ata/sd entries repeating)"
date: 2009-02-24
forum: General Help
---

### Post by jnorth on 2009-02-24
Guys - looking for assistance here.

As of a couple days ago, my syslog and dmesg have begun writing crazy numbers of lines  - repeating the following entries over and over again.

I'm clueless right now.  I've been searching but can't find any errors on this.  I mean these are the same entries that pop up on boot when my drives are discovered, so nothing looks out of the ordinary except the fact that it is repeating every second.

Any ideas?

```
Feb 24 15:17:55 mc01 kernel: [317524.281085] sd 8:0:0:0: [sdf] 240121728 512-byte hardware sectors (122942 MB)
Feb 24 15:17:55 mc01 kernel: [317524.281283] sd 8:0:0:0: [sdf] Write Protect is off
Feb 24 15:17:55 mc01 kernel: [317524.281286] sd 8:0:0:0: [sdf] Mode Sense: 00 3a 00 00
Feb 24 15:17:55 mc01 kernel: [317524.281594] sd 8:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 24 15:17:55 mc01 kernel: [317524.281826] sd 8:0:1:0: [sdg] 976773168 512-byte hardware sectors (500108 MB)
Feb 24 15:17:55 mc01 kernel: [317524.282017] sd 8:0:1:0: [sdg] Write Protect is off
Feb 24 15:17:55 mc01 kernel: [317524.282020] sd 8:0:1:0: [sdg] Mode Sense: 00 3a 00 00
Feb 24 15:17:55 mc01 kernel: [317524.282322] sd 8:0:1:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 24 15:17:57 mc01 kernel: [317525.860425] ata9.00: configured for UDMA/133
Feb 24 15:17:57 mc01 kernel: [317525.868458] ata9.01: configured for UDMA/133
Feb 24 15:17:57 mc01 kernel: [317525.868466] ata9: EH complete
Feb 24 15:17:57 mc01 kernel: [317525.868540] sd 8:0:0:0: [sdf] 240121728 512-byte hardware sectors (122942 MB)
Feb 24 15:17:57 mc01 kernel: [317525.868635] sd 8:0:0:0: [sdf] Write Protect is off
Feb 24 15:17:57 mc01 kernel: [317525.868638] sd 8:0:0:0: [sdf] Mode Sense: 00 3a 00 00
Feb 24 15:17:57 mc01 kernel: [317525.868879] sd 8:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 24 15:17:57 mc01 kernel: [317525.869131] sd 8:0:1:0: [sdg] 976773168 512-byte hardware sectors (500108 MB)
Feb 24 15:17:57 mc01 kernel: [317525.869253] sd 8:0:1:0: [sdg] Write Protect is off
Feb 24 15:17:57 mc01 kernel: [317525.869259] sd 8:0:1:0: [sdg] Mode Sense: 00 3a 00 00
Feb 24 15:17:57 mc01 kernel: [317525.869505] sd 8:0:1:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 24 15:17:58 mc01 kernel: [317527.444383] ata9.00: configured for UDMA/133
Feb 24 15:17:58 mc01 kernel: [317527.460421] ata9.01: configured for UDMA/133
Feb 24 15:17:58 mc01 kernel: [317527.460426] ata9: EH complete

```

---

