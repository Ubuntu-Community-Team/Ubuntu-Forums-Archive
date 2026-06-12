---
title: "how to change password"
date: 2005-09-07
forum: Desktop Environments
---

### Post by AndrewStout on 2005-09-07
So just now on my new Ubuntu 5.04 install, I decided I wanted to change my [user account] password.  I did System->Administration->Users & Groups, selected my user account [the only one], clicked properties, highlighted the password field, typed my new password, did the same to confirm, clicked OK a couple times to exit the GUI tool thingy.

Logged out, went to log back in, and neither old password nor new password worked.

I'm getting better about not panicking in situations like this, and I rebooted, selected the recovery mode entry from GRUB (glad I left that in when I modified my GRUB configuration...), ran passwd as root to fix my [user account] password, rebooted, and all was well.

But this makes me wonder: did I do something wrong?  I would have expected the friendly GUI Users & Groups interface to be the recommended way to change a password.  Why was it so easy for me to screw mine up?

learning my way around linux administration and Ubuntu,
--Andrew

---

### Post by djib on 2005-09-07
Hello,
Maybe you had Caps-lock enabled when you typed your password. You would have then typed the same password twice, but not the one you wanted...

---

