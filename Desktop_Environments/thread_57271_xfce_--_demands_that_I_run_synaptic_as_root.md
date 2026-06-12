---
title: "xfce -- demands that I run synaptic as root"
date: 2005-08-15
forum: Desktop Environments
---

### Post by j.hill on 2005-08-15
If I'm using the default GNOME desktop, Synaptic asks for my password, in keeping (I suppose) with the Ubuntu sudo convention.  If I'm working in xfce, though, it refuses to run Synaptic, saying that I need to be logged in as root.

Now I know the workaround for this:  type ```
sudo synaptic
``` in a terminal.  But is there a way to get xfce to do things the Ubuntu way, and let me run Synaptic with sudo?

---

### Post by nuno on 2005-08-15
In the Desktop put a icon with the comand    gksudo synaptic

---

### Post by recce101 on 2005-08-15
I was playing around with Xfce earlier today, and managed to create a launcher that opens Synaptic as root. Here's how:

Right-click on one of the icons down in your Xfce panel, choose "Add new item," select "Launcher," and click "Add," In the Command box put "gksudo synaptic" and type "Synaptic" or whatever you want in the Tooltip box, then close. The first time you run it you might be asked for your password, which will be your regular User password (you probably don't have a Root password -- I don't).

Being a newbie, I don't really know what the "gk" in front of sudo is for (just remembered it from something I read), but it seems to work every time. Sometimes just "sudo synaptic" will work, but usually not, don't know why. I also created launchers for Root Terminal (command is "gksudo xfterm4") and Root File Manager (command is "gksudo rox") which come in handy.

Let us know how it works for you. I REALLY like the Xfce file manager, find it easier and more capable than what KDE and Gnome offer. And the Xfce desktop comes up so much quicker with no errors or hangups.

---

### Post by j.hill on 2005-08-16
[QUOTE=recce101]The first time you run it you might be asked for your password, which will be your regular User password (you probably don't have a Root password -- I don't).[/QUOTE]

Oddly enough, I do have a root password.  I think I'm the only Ubuntisto who does.  The installer created a root account, but did *not* put me on the sudo list -- i.e., it did just the opposite of what it ought.  Easily corrected, but still puzzling.

---

