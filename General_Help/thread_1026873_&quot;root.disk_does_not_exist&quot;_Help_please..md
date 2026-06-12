---
title: "&quot;root.disk does not exist&quot; Help please."
date: 2008-12-31
forum: General Help
---

### Post by printarg on 2008-12-31
I just booted up Wubi and got this:

Loading, please wait...
ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell.

Is there a recovery for this or should I just remove and reinstall?

Is there a way to run Ubuntu as a Windows process or perhaps in a VM? Just so I don't have to reboot every time I want Linux.

Thanks.

---

### Post by Jammanuser on 2008-12-31
> **printarg said:**
> I just booted up Wubi and got this:

Loading, please wait...
ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell.

Is there a recovery for this or should I just remove and reinstall?


Well...as the root.disk constitutes your whole Ubuntu OS, stored neatly inside, you will need a whole new root.disk! ;)

And the only way to obtain one, if you haven't backed it up while it was still working (btw, maybe you should do that next time...), is to run the Wubi installer again, unless you happen to have a friend who runs Wubi, who might be willing to let you copy his root.disk, and transfer it over to your computer! :) Of course, then that means you will get all his private documents and files in the process...and he probably wont want that! :lol:

Cheers! :popcorn:

-jam man

:guitar:

---

### Post by printarg on 2008-12-31
I did a reinstall and got the same message!

---

### Post by Jammanuser on 2009-01-01
> **printarg said:**
> I did a reinstall and got the same message!

hmm...where did you download it from? If it wasn't from [here]("http://www.wubi-installer.org"), then I would suggest downloading it from that link instead, and try it again! ;) It is quite possible either the file was corrupt to begin with, or the download got messed up somehow. So I would suggest downloading it again, from the site I just gave you, and hopefully that will fix it! :P

Cheers! ):P

-Jam man

:guitar:

---

### Post by abn91c on 2009-01-01
> **printarg said:**
> I just booted up Wubi and got this:

Loading, please wait...
ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell.

Is there a recovery for this or should I just remove and reinstall?

Is there a way to run Ubuntu as a Windows process or perhaps in a VM? Just so I don't have to reboot every time I want Linux.

Thanks.
That happens when you don't have a clean re-start in the computer, so Ubuntu does not mount the drive, the solutions is to reboot to windows first then restart the computer from windows(Do not press the re-set button) and select ubuntu at the promt like normal.

---

### Post by hyperdude111 on 2009-01-02
wubi is very unreliable. I used to have problems on boot every week until a switched to a partition.

---

### Post by tpe11etier on 2009-01-02
abn is correct.  This happens to me if I just power the machine down during a hangup.  If you boot fully into windows, shut down, then boot back into ubuntu, you *should* be fine...

---

