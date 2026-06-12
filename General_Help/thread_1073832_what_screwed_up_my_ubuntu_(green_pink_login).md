---
title: "what screwed up my ubuntu (green pink login)"
date: 2009-02-18
forum: General Help
---

### Post by foges on 2009-02-18
I havn't installed any software recently except for updates and suddenly i get this (when i start my computer up, everything was fine before the last shutdown):

[IMG]http://img14.imageshack.us/img14/4328/photo218sb0.jpg[/IMG]
(yes its mirrored, due to photobooth)

Any ideas? this is my login screen, i can enter my username and password and i hear that im logged in, but if i for example press alt+f2 it restarts

---

### Post by theDaveTheRave on 2009-02-18
Very strange stuff...

can you boot into the command line or into the "recovery" kernel, or any other kernel from the grub menu for that matter?

David

if you can get a live cd or a console can you get a copy of dmesd or /var/log/syslog ?

they may be usefull?

---

### Post by Yashiro on 2009-02-18
Which video chipset do you have and what drivers were you using?

---

### Post by Nexusx6 on 2009-02-18
Uh oh. This could be a dead or dieing monitor. If you have another monitor that you use from another computer, or small LCD a friend could bring over/you grab for a minute, it would be a pretty sure fire way to confirm or dismiss your monitor from being the problem.

---

### Post by foges on 2009-02-18
syslog: [http://codeviewer.org/view/code:64e](http://codeviewer.org/view/code:64e)

dmesg: [http://codeviewer.org/view/code:64f](http://codeviewer.org/view/code:64f)

no idea what that means... got that from the live CD, i can get into the recovery menu from crub, and that above was from a live CD.

Yashiro: I have an ATI 3450, downloaded the drivers from the ati website and installed them because the restricted drivers did NOT work. I'd say its most likely that this is the problem, if i remember correctly, one of the recent updates had something to do with restricted drivers.

Nexusx6: I highly doubt its my monitor, booting from the live CD went just fine and i dont think my monitor is capable of shutting down my pc...?

Thanks guys for the quick response

---

### Post by Yashiro on 2009-02-18
Try running the xfix mode from the recovery boot mode.
If that works ok, uninstall all your ati drivers. (using the uninstall fglrx script and then synaptic if need be)

Then install the latest ati crud. Make sure you have 'dkms' installed too.

---

### Post by foges on 2009-02-19
wonderful, that seemed to have worked, even the restricted drivers work now :) thanks a bunch

---

### Post by Yashiro on 2009-02-19
Glad it worked first try. Getting video drivers to work on Linux is a huge pain in the bum.

Next time you have some updates to apply, if any of them involve a kernel update be aware that this may happen again.
If you have dkms installed it should solve this, if not you'll just have to install your vid drivers again after a kernel update.

---

