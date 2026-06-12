---
title: "printer detection"
date: 2005-03-29
forum: Desktop Environments
---

### Post by lee_connell on 2005-03-29
if i plug in my usb printer its detected.  is there a way i can get the gnome print manager to pick it up without having to reboot the computer?

---

### Post by andreizinca on 2005-08-06
Since cupsys is the daemon that handles printers, you should write the folowing in a console:

sudo /etc/init.d/cupsys force-reload

---

### Post by mlissner on 2006-02-02
[QUOTE=andreizinca]Since cupsys is the daemon that handles printers, you should write the folowing in a console:

sudo /etc/init.d/cupsys force-reload[/QUOTE]
I can get this command to work, but I can only get my printer to actually be detected if I restart. I don't get it. Why doesn't something happen when I plug it in? What would it take to make ubuntu realize that I've plugged a printer in without forcing me to restart to print!

Thanks in advance.

---

### Post by mlissner on 2006-03-09
Hey, this was weeks and months ago that I posted this problem with no resolution. Does anybody have any ideas as to why when I plug in the USB cord on my printer, nothing happens at all?

I really would like to be able to plug and unplug without restarting all the time, and that solution doesn't work...

Thanks again.

---

