---
title: "Unneeded packages"
date: 2004-12-05
forum: Desktop Environments
---

### Post by humina on 2004-12-05
I notice when my computer starts up there are services running that I do not need.  For example there are services for RAID and Enterprise Volume Management.  I've got 2 hard drives in my computer.  1 has ubuntu on it and the other has my games (windows).  I obviously do not have a raid.  I'm not an enterprise and I shouldn't need an enterprise volume manager to keep track of my 2 drives (unless the enterprise volume manager does something unknown to me and important for my system).

Can someone tell me which packages are safe for me to remove so that I am not starting unnecessary daemons or performing unnecessary tasks at boot.  Perhaps there is a speed up your boot FAQ that I missed somewhere in the forums.  Thanks.

---

### Post by saBrEwolf on 2004-12-05
I've seen this too..
The services you don't need depends on what you're doing.. for example, you don't need portmap if you're not doing NFS installs. Another would be the rsync daemon.. You don't need that ulness your rsyncing things.. I wouldn't recommend removing the Enterprise Volume Management system as I'm not sure as to what that does myself.

Hope this helps

---

### Post by calamari on 2004-12-06
[QUOTE=saBrEwolf]I've seen this too..
The services you don't need depends on what you're doing.. for example, you don't need portmap if you're not doing NFS installs. Another would be the rsync daemon.. You don't need that ulness your rsyncing things.. I wouldn't recommend removing the Enterprise Volume Management system as I'm not sure as to what that does myself.

Hope this helps[/QUOTE]
 Agreed.  Hope this problem is fixed soon.  It would be very nice to be able to uninstall things.  I was told that if I uninstalled anything that Ubuntu installed for me that if I tried to upgrade to Hoary it wouldn't work right and I wouldn't get Xorg, etc.  So I have a bunch of useless programs on my HD because I'm afraid to remove them.  Reminds me a lot of the Windows "can't uninstall" IE thing, hehehe.

Jeff

---

### Post by az on 2004-12-06
" It would be very nice to be able to uninstall things. I was told that if I uninstalled anything that Ubuntu installed for me that if I tried to upgrade to Hoary it wouldn't work right and I wouldn't get Xorg, etc"

What a load of crap.  You can uninstall whatever you want.  You can resinstall it too!  If you do a dist-upgrade to Hoary (when it becomes stable) and it does not pick up xorg, you just tell it to install it!  WHat is the problem here?  The whole advantage of debian packaging is that you can easily install and remove things.

---

