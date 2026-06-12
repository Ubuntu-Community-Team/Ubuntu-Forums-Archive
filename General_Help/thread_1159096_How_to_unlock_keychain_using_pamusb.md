---
title: "How to unlock keychain using pamusb"
date: 2009-05-14
forum: General Help
---

### Post by SuperOmegaSlack on 2009-05-14
I have followed the tutorial to use an sd card as login credential using pamusb here:
[http://ubuntuforums.org/archive/index.php/t-17571.html](http://ubuntuforums.org/archive/index.php/t-17571.html)

Login authentication works, screensaver locks when the card is removed and unlocks when I reinsert it... But every time I login, NetworkManager wants to access the keyring and asks for a password to unlock it.

My question... How can pamusb unlock the keyring upon login?

I have looked around for an answer but all I have found are people with the same question and no answer.

Asus EEEpc 1000HA
Ubuntu 9.04

---

### Post by Lazaruss on 2012-04-26
3 years later I have an answer for you :)

Of course, this depends on how security conscious you are, as it involves leaving the password for your keyring as plaintext in a script...

1. Get the python-gnomekeyring package
2. Edit the script below with the correct names and passwords for your keyring(s)
3. Save it in a logical place and chmod it to 700 (i.e. `chmod 700 <scriptname>`)
4. Add the script to your startup applications

Script:
```

#!/usr/bin/env python2

import pygtk
import gnomekeyring
import sys

gnomekeyring.unlock_sync('login','<password>')
gnomekeyring.unlock_sync('<keyring>','<password>') # Repeat for each keyring you need unlocked automatically

sys.exit(0)

```

---

### Post by oldos2er on 2012-04-26
Old thread closed.

---

