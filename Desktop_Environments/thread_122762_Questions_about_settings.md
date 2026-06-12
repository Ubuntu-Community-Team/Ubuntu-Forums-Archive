---
title: "Questions about settings"
date: 2006-01-28
forum: Desktop Environments
---

### Post by psilo357 on 2006-01-28
I just installed ubuntu on my system a couple days ago, and am starting to get a pretty good feel for it.  The main problem that i am having is if i boot back into windows to do some gaming, then come back to Ubuntu, all of my setup has dissappeared.  I lose my desktop wallpaper, i have made some files which look onto my second harddrive, Formatted Fat32(so i can use it with windows and linux for my mp3, mpeg, jpeg, and what not.  These files will be empty when i come back, but still on the desktop, and i have to set them up again using disk tools.  The last question is with setting up the printer, i have an hp 6210 and i cant seem to get it to work, any help would be appreciated>

peace

---

### Post by stalefries on 2006-01-28
Check here ([http://www.linuxprinting.org/printer_list.cgi?make=HP](http://www.linuxprinting.org/printer_list.cgi?make=HP)) for your printer. If it isn't there try doing some googling. Check the HP website. I hear that they provide CUPS drivers almost the same time they release printers. Fun!

I have no idea about your other problem, though. Sorry.

---

### Post by psilo357 on 2006-01-29
bumping this thread up, i figured out the problem with the desktop not keeping the same bacground, i had to extract the image to a different file than tmp, does it get erased or something everytime i restart? that is my quess......also, the files i set up that let me into my second 160GB harddrive will not stay set up, i have to redo them everytime i start up still....only takes like 20 seconds, but still annoying......also, i cant seem to change the priveleges on those files that i set up, i need read/write capabilites on there, but it wont let me write to them, only read, ive changed the owner of the file on the desktop, but its nested file says that permission is denied or something along those lines, but even as the owner, it wont let me change the permissions, help on this would be great too, sorry for all the questions, but thanks for all the help

peace

---

### Post by psilo357 on 2006-01-29
bump yet again, any ideas????

---

### Post by dcstar on 2006-01-29
[QUOTE=psilo357]I just installed ubuntu on my system a couple days ago, and am starting to get a pretty good feel for it.  The main problem that i am having is if i boot back into windows to do some gaming, then come back to Ubuntu, all of my setup has dissappeared.  I lose my desktop wallpaper, i have made some files which look onto my second harddrive, Formatted Fat32(so i can use it with windows and linux for my mp3, mpeg, jpeg, and what not.  These files will be empty when i come back, but still on the desktop, and i have to set them up again using disk tools........
[/QUOTE]
You have to set up an entry in you /etc/fstab file to mount your other disk on bootup.

Do a forum search on "mounting windows" and you should find the answers.

---

### Post by RAOF on 2006-01-29
[QUOTE=dcstar]You have to set up an entry in you /etc/fstab file to mount your other disk on bootup.

Do a forum search on "mounting windows" and you should find the answers.[/QUOTE]
Or even better, check [the wiki page]("https://wiki.ubuntu.com/AutomaticallyMountPartitions?action=show&redirect=AutomaticallyMountMSWindowsPartitions").

---

### Post by ubuntu27 on 2006-01-29
[QUOTE=psilo357]bumping this thread up, i figured out the problem with the desktop not keeping the same bacground, i had to extract the image to a different file than tmp, does it get erased or something everytime i restart? ...
peace[/QUOTE]

Did you do this?

[http://ubuntuguide.org/#cleantmpfoldershutdown](http://ubuntuguide.org/#cleantmpfoldershutdown)

---

