---
title: "Kontact won't send/receive messages."
date: 2005-11-01
forum: Desktop Environments
---

### Post by derrick1985 on 2005-11-01
Yes, I know this is in the Ubuntu forum.

Anyways, Kontact/Kmail will not let me send/receive messages anymore. It's my fault, i know that but I need help fixing it. I had Kubuntu installed and found that I didn't like it as much as Gnome, so I downloaded Ubuntu Desktop and started removing some of the kde packages. I think I removed the package for sending/receiving messages, and I need to know which one it is to get it working!

The error I receive is "Could not start process pop3"

HELP!

---

### Post by Manny C on 2005-11-01
I hope you used Synaptic to remove kde packages. Synaptic records package install/remove history. ;)

So did you use Synaptic?

---

### Post by derrick1985 on 2005-11-01
[QUOTE=Manny C]I hope you used Synaptic to remove kde packages. Synaptic records package install/remove history. ;)

So did you use Synaptic?[/QUOTE]

Yes... yes I did....

---

### Post by lorenco on 2005-11-01
You might want to remove kmail and re-install it.  Make sure you make a backup of ~.kde/share/apps/kmail 

You might also try to move the above directory to a backup location and copy the mail directory after setting up again (if you require your old mail)

Give it a bash... would also try to reinstall kdepim (breezy) This is the meta package the installs kmail. Give it a bash. You might also do the win thing and re-install ;) if all else fails... (Kidding)

---

### Post by derrick1985 on 2005-11-01
[QUOTE=lorenco]You might want to remove kmail and re-install it.  Make sure you make a backup of ~.kde/share/apps/kmail 

You might also try to move the above directory to a backup location and copy the mail directory after setting up again (if you require your old mail)

Give it a bash... would also try to reinstall kdepim (breezy) This is the meta package the installs kmail. Give it a bash. You might also do the win thing and re-install ;) if all else fails... (Kidding)[/QUOTE]

God no, not reinstall! I FINALLY have it working the way I want to, last thing I want to do is crash it (again, that would be the third time)

Oh well, I broke down and reinstalled kubuntu-desktop, works fine now too (before thatI did try reinstalling kmail/kontact, that didn't work either)

Thanks again. Now, If i can only get this stupid winxp theme to work in kde, I might be able to convert a few people to the light side of the force.

Thanks.

Derrick

---

### Post by rusyear04 on 2006-11-17
for the **pop3-error** under **gnome**:
check out this thread

[http://www.ubuntuforums.org/showthread.php?t=200623&page=2](http://www.ubuntuforums.org/showthread.php?t=200623&page=2)

best regards :mrgreen:

---

### Post by ArcherB on 2008-02-28
> **derrick1985 said:**
> Yes, I know this is in the Ubuntu forum.

Anyways, Kontact/Kmail will not let me send/receive messages anymore. It's my fault, i know that but I need help fixing it. I had Kubuntu installed and found that I didn't like it as much as Gnome, so I downloaded Ubuntu Desktop and started removing some of the kde packages. I think I removed the package for sending/receiving messages, and I need to know which one it is to get it working!

The error I receive is "Could not start process pop3"

HELP!

Don't know if you still need help with this, but this worked for me...

Open a terminal and type the following:
[INDENT]dcopserver_shutdown
kdeinit[/INDENT]

Then relaunch Kontact.

---

