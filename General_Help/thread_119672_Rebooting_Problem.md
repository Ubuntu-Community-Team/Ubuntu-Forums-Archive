---
title: "Rebooting Problem"
date: 2006-01-20
forum: General Help
---

### Post by carter4life on 2006-01-20
Hello, I am new to Ubuntu, also I am new to Linux. My problem is whenever I try to reboot my computer, it shuts down instead of rebooting. Any help is appreciated thanx.

---

### Post by darth_vector on 2006-01-20
open a terminal and try```
sudo shutdown -r now
```that should reboot your machine.

---

### Post by Reg on 2006-01-20
hi,
I'm new too, and my Ubuntu won't reboot at all. I have to close down. Any ideas please?
Thanks
Reg

---

### Post by Elrond on 2006-01-20
Try typing ''sudo reboot''.

It works for me fine.

---

### Post by carter4life on 2006-01-20
I tried that "sudo shutdown -r now"; command didn't work.

---

### Post by hillbilly on 2006-01-20
What does the command say ? Is any error message displayed. Maybe you havent set your path properly. Try > sudo /sbin/shutdown -r now

---

### Post by Reg on 2006-01-25
Thanks. Yes, with the terminal it does reboot. But when I use the usual shutdown/reboot alternative, it doesn't. It just hangs there with a blank screen.
Reg

---

### Post by hillbilly on 2006-01-25
One thing you could do is check what command is being run when you actually click on the shutdown tab. Iam not sure of the exact location of gdm. it should be somewhere in /etc/rc.d or something.  You can find it out by
> find /etc -name gdm 2>/dev/null 

So once inside gdm you could check what command is being run.

---

### Post by hillbilly on 2006-01-25
Oops I guess you meant shutting down from inside gnome. Well this case you would have to find the config file for the menu. Not sure where this is though.

---

### Post by Reg on 2006-01-26
I've found the gdm file in /etc
The relevant line seems to be:
RebootCommand=/sbin/shutdown -r now \"Rebooted from gdm menu.\"

Is this correct?
Thanks
Reg

---

