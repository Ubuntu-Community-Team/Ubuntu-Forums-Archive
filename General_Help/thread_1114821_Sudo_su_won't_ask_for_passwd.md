---
title: "Sudo su won't ask for passwd"
date: 2009-04-03
forum: General Help
---

### Post by johannes_h on 2009-04-03
I wrote something like chmod +s /bin/su .. hehe .. how to I put it back to default? :) Now when I write sudo su it just logges right in :S

Thanks !

---

### Post by Tobi-fp on 2009-04-03
try rebooting, it might remember the password, but anyways, what is the problem? if you are logged in you can perform the action

---

### Post by hyper_ch on 2009-04-03
(1) sudo given password will be remember for some time... if you issue sudo again you will not be asked and the time to expire will be pronlonged

(2) don't use sudo su but use sudo -i

---

### Post by johannes_h on 2009-04-03
Thanks

---

