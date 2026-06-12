---
title: "default keyring locked?"
date: 2006-04-27
forum: Desktop Environments
---

### Post by nthwaver on 2006-04-27
I'm running 5.10 with GNOME, and regularly access Samba shares elsewhere on our LAN.  My connection to the shares (using Places >> Network Servers >> Windows Network) occasionally goes haywire, but usually sets itself right again.  This time, however, whenever I try to open "Network Servers" I get a spinning cursor, and Ubuntu tells me this:

   Enter password for default keyring to unlock
   The application "File Manager" (/usr/bin/nautilus) wants
   access to the default keyring but it is locked.

None of my known passwords will satisfy this message.  I am still able to use "Connect To Server" and specify the host name, but I can no longer browse without mounting.

I tried researching this and read the thread on this forum a few weeks ago.  I don't have keyring manager installed and I don't want to, as I haven't had this problem in the past.  I tried renaming /home/me/.gnome2/keyrings/default.keyring but I was not prompted for a new password, just given the same message to which there is no satisfactory answer.

Should I change permissions on default.keyring?  That doesn't seem like the smartest idea.  Why is this only now becoming an issue?

Thanks!

---

### Post by ifrflyer on 2006-05-05
Instead of renaming that file try removing that file default.keyring and try again

---

### Post by Stryker777 on 2006-05-09
Thanks for that quick easy answer ifrflyer.  My password wouldnt work either so I deleted and it rebuilt just fine.

---

