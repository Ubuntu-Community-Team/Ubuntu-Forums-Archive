---
title: "Automount stopped working after installing wine / dvdfab / dvdshrink"
date: 2006-06-14
forum: Desktop Environments
---

### Post by Tazix on 2006-06-14
Hello.

Gotta say that Xubuntu has got to be the first distro I've *completely* liked, "out of the box".  Great stuff!

Anyway... I installed the latest wine from winehq, 0.9.12, and installed dvdfab and dvd shrink. (Following the instructions from various threads in these forums).

Now when I stick a DVD or an Audio CD in, the XFCE automount doesn't work anymore (No desktop icon, or icon flashes up for a second), but a data cd still does.

DVDfab still works if I manually mount the DVD in a terminal window first.

I assume wine is the culprit, since that's been the only native linux software "change". Is there any way to fix the XFCE automount after installing wine?

Thanks,

Taz

---

### Post by mindwarp on 2006-06-14
Try this: [post]1070905[/post]

---

### Post by Tazix on 2006-06-14
[QUOTE=mindwarp]Try this: [post]1070905[/post][/QUOTE]

Thanks for the reply.

That solution looks like it's for Ubuntu with the GNOME desktop.  Will that mess up my XFCE desktop?

If not... I'll try it when I get home from work.

-Taz

---

### Post by Tazix on 2006-06-14
That solution isn't going to work for me.  I checked the packages I have installed, both on the machine in question, and another one that has no automount problem (yet)... none (other than hal) of those packages are installed (to be removed), and I'm not installing a bunch of gnome stuff on my XFCE.

Remember.... this is Xubuntu... not Ubuntu.

Doing a search on this forum for "automount", does show that it's a Dapper problem... with a different solution for Ubuntu and Kubuntu... but none yet for Xubuntu.

-Taz

---

### Post by Tazix on 2006-06-15
Well... I got it fixed... not sure why what I did fixed it... maybe someone with more knowledge can explain it to me.

First "Automount" may be an inappropriate term...  When you stick a DVD, CD or USB Drive in... an Icon appears on the XFCE desktop.  You still have to either double click the icon or right-click and open / mount.

Xubuntu (by default) doesn't have either ivman or gnome-volume-manager running to "automount".

Anyway... How I broke it:

After installing wine (following an ubuntu howto)... I added the dosdevice D: as /media/cdrom.  Well, in Xubuntu... that's a symbolic link to /media/cdrom0, which is the actual mount point.

Anyway... that messes with XFCE somehow.  I don't exactly know why... because even after rebooting... no wine apps are running, and wine isn't in the processes list.  And I don't see how putting in an Audio CD or Movie DVD would invoke wine in any way. (Remember... Data CD's were still working).

Anyway... How I fixed it:

~Went into /home/<user>/.wine/dosdevices and deleted the D: symbolic link.
~Ran wincfg and re-added the D: dos device, except pointing to /media/cdrom0/
~Hit Ctrl-Alt-Backspace to restart X.

Voilla... Fixed.

-Taz

---

### Post by mindwarp on 2006-06-17
Thanks for posting the fix for other users that may run into similiar issues.

---

