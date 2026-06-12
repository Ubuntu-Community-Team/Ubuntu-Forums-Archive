---
title: "K3b Startup Issue"
date: 2007-11-03
forum: Desktop Environments
---

### Post by Paul Gilster on 2007-11-03
About a month ago I burned a few data CDs without problem using K3b (I was using Feisty then and still am). This morning I tried to burn another and got this message: No CD/DVD writer found. Tried running as root and this doesn't work either, so I assume it's not a matter of permissions. I assume an update to K3b caused this problem, but does anyone know what I should do to fix it?

Thanks,

Paul

---

### Post by Thyme on 2007-11-03
Hi Paul,

Are you able to browse DVD's when you put one in your writer? Also, does k3b pick up your writers in the "preferences" menu (or some options related menu)?

---

### Post by TeaSwigger on 2007-11-03
> **Paul Gilster said:**
> About a month ago I burned a few data CDs without problem using K3b (I was using Feisty then and still am). This morning I tried to burn another and got this message: No CD/DVD writer found. Tried running as root and this doesn't work either, so I assume it's not a matter of permissions. I assume an update to K3b caused this problem, but does anyone know what I should do to fix it?

Thanks,

Paul

Hello Paul, well first thing I'd do is confirm that the system as a whole is still recognizing the drive. Put in a disc, CD or DVD, browse to /media/ and see if it's there, if it's useable etc. If not, look into getting the drive detected and mounted again. If it is ok, try the k3b setup utility to eliminate possible permissions issues.

---

### Post by Paul Gilster on 2007-11-06
Thanks, guys. I never could get K3b working again, but finally decided it was time for the Gutsy move anyway and went ahead with that. No problems burning CDs since the upgrade.

---

