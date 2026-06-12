---
title: "More TWEAKs for Kubuntu users!"
date: 2005-03-25
forum: Desktop Environments
---

### Post by vvu on 2005-03-25
_Get your current settings for hda (your first drive in this sample and IDE)_
# **hdparm /dev/hda**  <-- actual codes to type (not the #)


_Actual code for optimizations:_

# **hdparm -W1 /dev/hda**
# **hdparm -qm8 -qu1 -qc1 -qd1 /dev/hda**  - you may not need everything here if some are already enabled.

_Explanation:_

# -qm8 Set multiple sector count to 8
# -qu1 Set unmaskirq flag on
# -qc1 Set 32-bit IO on
# -qd1 Set DMA on
# -W1 Enables write caching

Be ready for faster access!

Also, make sure to **review **the MAN pages for  hdparm as it may BLOW your drive up  :shock:

---

