---
title: "Mounting floppy with the &quot;Disk Mounter&quot; applet"
date: 2006-06-16
forum: Desktop Environments
---

### Post by superbiskit on 2006-06-16
It wasn't always this way, but I lost track of which "improvement" caused it.

If I attempt to mount my floppy using the Gnome Disk Mounter applet, I get an error message:
"The given UDI is not a mountable volume."  Surely among the most unhelpful messages in the book.

I can, however, do "pmount -t vfat /media/floppy0" from a command line (and give a script & launcher to my dear wife so she can use the floppy too).

We are both members of group "floppy"
The /etc/fstab line reads:
/dev/fd0 /media/floppy0 vfat users,rw,noauto 0 0 

Any help will be most welcome.

---

### Post by talent on 2006-06-17
I am new ubuntu user since today and my floppy is unmounted "UDI is not a mountable volume" , with windows floppy is work so what shut I do?

---

### Post by DoktorNo on 2006-06-18
This issue was discussed here:
[http://www.ubuntuforums.org/archive/index.php/t-76517.html]("http://www.ubuntuforums.org/archive/index.php/t-76517.html")

I bet, that the best way to solve this bug, is tu update the pmount package to version 0.9.6. Go to Synaptic, then go to Repository settings, and then add the breezy-backports repository. Then search for pmount package in this version.

Of course, there are other solutions metioned in this thread, so go figure witch suits you the best.

---

### Post by superbiskit on 2006-06-19
Well, thanks.  I installed "pmount=0.9.6-1~breezy1" [sic] from breezy-backports.  It was also necessary to add my real users to the "plugdev" group where pmount runs -- otherwise the system refuses to run pmount for the user.  Don't know how that could have been automated.

---

