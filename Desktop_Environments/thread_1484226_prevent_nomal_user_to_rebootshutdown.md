---
title: "prevent nomal user to reboot/shutdown"
date: 2010-05-15
forum: Desktop Environments
---

### Post by lo.j on 2010-05-15
hello everyone.
i searched the forum about this subject, i found many post but nothing useful.

i also wonder why a normal user is not prompted to authenticate as root to perform these tasks.

i thought the file /etc/sudoers but i don't think this is the point.
i tried the group "shutdown" but does not exist.

i read that this is expected in ubuntu server so it should exist even in the desktop version, i guess.

waiting for suggestions,
thanks a lot.

---

### Post by mcduck on 2010-05-15
For most desktop users requiring a password to reboot/shutdown would be ridiculous (not to mention that they would be able to do that anyway simply by holding down the power button for couple of seconds). The ability to do this is provided by GDM (something that I learned while figuring out how to shutdown the system from Openbox), while any terminal command to shutdown *does* require root privileges.. 

But if you are running a multiuser system or a kiosk setup and need to prevent normal users from shutting down then this is probably what you are looking for: [http://embraceubuntu.com/2006/03/20/disable-shutdown-for-normal-users/]("http://embraceubuntu.com/2006/03/20/disable-shutdown-for-normal-users/")

edit: note that at least the last step in that guide isn't actually required in Ubuntu, since the shutdown command already requires root permissions.

---

### Post by lo.j on 2010-05-15
thanks for the answer.
i also think i came across some of your posts on the subject...

yes, i already read that post but i also noticed that it was published in 2006 ... is still relevant and reliable for ubuntu 4.10?

for example i don't have any /etc/X11/gdm folder... :)

thanks again...

---

### Post by mcduck on 2010-05-15
Good point about the post being an old one, some things in it ares still valid but for example GDM configuration has changed quite a bit since then, as we are now using GDM2...

I tried to search a bit, but couldn't find any guides that would work as they are on 10.04. I'll tell you if I figure anything out, but I can't really promise anything as I'm not that familiar with the GDM2 configuration in 10.04...

(at least the ACPI powerbutton stuff in that article is still valid, so if you want you can start by doing that...)

---

