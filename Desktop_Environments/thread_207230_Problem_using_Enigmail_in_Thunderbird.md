---
title: "Problem using Enigmail in Thunderbird"
date: 2006-07-01
forum: Desktop Environments
---

### Post by tgcUbuntu on 2006-07-01
I just installed the Enigmail extentsion for Thunderbird. When I ran Thunderbird the Enigmail OpenPGP wizard came up. When the wizard tried to access the ~/.gnupg directory there was a problem. I checked the permissions for the ~/.gnupg directory and only root has any access to it. (drwx------  2 root root        4096 2006-07-01 10:05 .gnupg).

Do I need to change the permissions on the .gnupg directory so that other users can access it? Or should I be setting things up logged in as root?


Thanks,
Ted

---

### Post by tgcUbuntu on 2006-07-01
I found the answer in another post here:
[http://www.ubuntuforums.org/archive/index.php/t-185584.html](http://www.ubuntuforums.org/archive/index.php/t-185584.html)

It looks like I had the permissions for the .gnupg directory set to root.
After changing them everything works now.

---

