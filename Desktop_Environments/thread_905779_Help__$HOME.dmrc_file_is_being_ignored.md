---
title: "Help : $HOME/.dmrc file is being ignored"
date: 2008-08-30
forum: Desktop Environments
---

### Post by Dreamerman on 2008-08-30
Hi. Last night I successfully mounted several drives but this morning, I can't log in properly. The error message after I login is as follows:-

"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users"

Can anyone help ?

Thanks

---

### Post by dacorr on 2008-08-30
try

 chmod 644 .dmrc

---

### Post by Dreamerman on 2008-08-30
Hey, thx for quick reply. I used [http://ubuntuforums.org/showthread.php?t=371052](http://ubuntuforums.org/showthread.php?t=371052) to solve my problem. Seems to do the trick & I don't see the error message anymore.

Thx again.

---

