---
title: "IBM Thinkpad T42 wireless dies"
date: 2005-06-15
forum: Desktop Environments
---

### Post by daveb1976 on 2005-06-15
Hi,

I've tried a couple of Ubuntu installs and thought perhaps I'd broken something with packages I'd installed, but after re-installing from scratch I've now seen the problem with a clean Ubuntu install:

After a period of time (which seems unpredictable), my wireless connection dies. The wireless ligiht on the T42 laptop goes out and after that there doesn't seem to be anything I can do to restore the connection other than reboot.

If I put the laptop into sleep mode and then restart, the wireless light goes back on, but the screen hangs so this doesn't help me.

Any ideas....?

---

### Post by xao on 2005-06-15
Do you have a power-save mode enabled on the wireless NIC?

---

### Post by daveb1976 on 2005-06-20
Hi.  I don't think so.  I've fiddled with various options in the BIOS to disable any powersaving, but no luck.

I wondered whether there was perhaps a powersave daemon running that was causing the problem.  It certainly doesn't happen under Windows.  I've tried restarting:

* powernowd
* inetd

Any other suggestions for how to restart the networking system?  I figure if restarting the laptop works, then there must be something that could reset the device?

Dave

---

### Post by bmontgom on 2005-07-25
[QUOTE=daveb1976]

Any other suggestions for how to restart the networking system?  I figure if restarting the laptop works, then there must be something that could reset the device?

[/QUOTE]

I believe this problem has to do with the ipw2200 drivers that come with Ubuntu.  The version of the drivers that come with the Ubuntu kernel are actually fairly old.  I downloaded and compiled the latest versions of the drivers and all my problems with the wireless have stopped.  You can get the drivers from [http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/).

---

