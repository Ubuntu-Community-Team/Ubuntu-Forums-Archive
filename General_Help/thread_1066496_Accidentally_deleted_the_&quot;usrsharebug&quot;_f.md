---
title: "Accidentally deleted the &quot;/usr/share/bug/&quot; folder"
date: 2009-02-10
forum: General Help
---

### Post by ouija on 2009-02-10
Ummm.... I accidentally removed the "/usr/share/bug" folder on my Ubuntu Hardy 64-bit installation.   I was cleaning up remnants from an uninstalled program, and was a little quick on the trigger when typing in a file location and name, and actually deleted the entire folder.

I've rebooted the system and ran a few programs but nothing seems to be affected.  I'm hoping that this won't cause any issues, but if so is there any way I can restore the files in this folder? Does Ubuntu have any native files located there after a clean install?

Let me know what I should do.   :)

---

### Post by sandyd on 2009-02-10
no damage done :)
you can go on with your ubuntu...
well unless your program gets buggy that is :)
youll find that you just lost everything that you would use for bug reports

in the future, please use an uninstallation script or sudo apt-get remove <appname>

---

### Post by ouija on 2009-02-10
Cool.  That's what I figured, just needed to make sure.

FYI: I would have used an uninstallation script or sudo apt-get remove <appname> but I was trying to remove a custom installation of Skype 32-bit off my 64bit OS, and there were no uninstall scripts nor did it show up in the package manager.

Also, just for peace of mind, I ended up booting the live cd of my install disk and copied the files located in the "/usr/share/bug" folder over to my main partition, using the command:

> sudo cp -r -preserve /usr/share/bug/* /media/disk/usr/share/bug

The files copied successfully and everything is running smooth.  I'm sure there are a few files missing for previous software installations, but if I run into any issues with them I'll simply re-install that particular program.

Thanks again!

---

