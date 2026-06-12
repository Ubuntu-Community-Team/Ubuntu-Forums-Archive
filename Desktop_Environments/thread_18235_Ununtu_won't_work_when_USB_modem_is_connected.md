---
title: "Ununtu won't work when USB modem is connected"
date: 2005-03-05
forum: Desktop Environments
---

### Post by DJcube on 2005-03-05
I am new to Linux, and installed it a few days ago, I managed to get my Speedtouh USB modem to work, and it was working until recently.

Now, when i try to load Linux hen the USB modem is plugged in, it wont work, and if  i connect the modem after it has lbooted up, Linux just crashes.

Does anyone know how to solve this problem?

---

### Post by alastair on 2005-03-05
If it stopped working - what changed?

For the boot up - press ESC to get to the grub menu. Then "e" to edit the kernel args (and perhaps "e" again?) - go to the end of the kernel line and take off the "quiet" option (if there).

Then "b" to boot.

See if you can see what messages are printed - where things "stop".

---

### Post by DJcube on 2005-03-07
It works fine when the computer is restarted, but when i start the computer straight into Linux from the computer beign shut down it doesnt work.

---

### Post by alastair on 2005-03-07
"It doesn't work" doesn't help anyone diagnose the problem though.

I asked about removing the "quiet" option on the boot command line - did you try this? You might see where it "stops".

Else - for crashes - what do the logs say?

/var/log/syslog

---

### Post by DJcube on 2005-03-09
The booting up just stops when it says "Loading hotplug Subsystem........" while booting up.

---

