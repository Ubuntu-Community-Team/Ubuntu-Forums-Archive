---
title: "Auto Mount Samba Share and put Icon on Desktop"
date: 2005-12-14
forum: General Help
---

### Post by ShiftyPowers on 2005-12-14
Hey all, I've managed to setup Samba on my ubuntu file server and can connect to the shares from other computers in my home.  However, on my main ubuntu rig (not the file server) I have to go through Places|Network Servers and then browse all the way through to the desired shared folder on the network.  Is it possible to have an icon on the desktop that automatically, upon boot or startup, mounts and links to that shared drive on the network?  This would save a lot of time....

Thanks

---

### Post by silex on 2005-12-14
Do you have the package smbfs installed?  smbfs has a tool caled smbmount that does what you're looking for; install smbfs and read the man page for smbmount to get a command to mount the samba share to a folder you create in /media, then use the Startup Programs tab in Gnome's Sessions tool (System>Preferences>Sessions) to add that command to what happens when Gnome starts.  I hope this helps, I don't have a samba share around right now to play around with, but this is something I have been looking into for myself but haven't gotten around to doing.

---

### Post by ShiftyPowers on 2005-12-14
awesome, i'll take a look at it.  Seems like the right program.  But pardon my ignorance, how do I see the man pages?

---

### Post by cstudent on 2005-12-14
If you click under Places menu and then use the Connect to Server option. Fill in the ip address of the server and share name, etc. You should get an icon on your desktop that will stay even when you reboot.

---

### Post by stuporglue on 2005-12-14
> But pardon my ignorance, how do I see the man pages?

Oh, you're going to love man pages. :-D

$ man $COMMAND

where $COMMAND is what you want to learn about

---

### Post by silex on 2005-12-14
[QUOTE=cstudent]If you click under Places menu and then use the Connect to Server option. Fill in the ip address of the server and share name, etc. You should get an icon on your desktop that will stay even when you reboot.[/QUOTE]

Ha, I remembered there was an easier way to do it than set up a smbmount.  Yea, the way Cstudent says to do it is all you'll ever need, but its good to know about the man pages as well; its usually the first place to look when you know what tool to use but not how to use it.

---

### Post by ShiftyPowers on 2005-12-14
is there a similar procedure in KDE? or is that Gnome only?

---

### Post by cstudent on 2005-12-14
[QUOTE=ShiftyPowers]is there a similar procedure in KDE? or is that Gnome only?[/QUOTE]

That would be for Gnome. I'm not sure about KDE. I haven't used KDE in a long time.

---

### Post by ShiftyPowers on 2005-12-14
wow, that really worked like a charm in Gnome, thanks guys

---

