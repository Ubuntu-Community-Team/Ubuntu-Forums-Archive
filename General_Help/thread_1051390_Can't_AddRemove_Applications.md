---
title: "Can't Add/Remove Applications"
date: 2009-01-26
forum: General Help
---

### Post by dingerkingh on 2009-01-26
I have a 64bit operating system and needed to install flash.  I found a how to example where it told me to copy the linux files over into the mozilla folder under /usr.  When I tried to copy them, it said I didn't have permission.  I found a script (naturally I can't find it again but it had something to do with typing in the /usr/mozilla/plugins and daren:daren) and it gave me the ability copy the files into that folder.  However, now I can't add or remove applications.  I think if I could undo what I did - it would work again.  I can't even install updates now.  Can anyone help? Moral of the story - dont do things when you don't know what you are doing lol.

---

### Post by dingerkingh on 2009-01-26
OH - and all it says in application failed to install.  I definitely broke something.

---

### Post by mb_webguy on 2009-01-26
You must have root priveleges to write to the /usr directory.  In the terminal, you can precede the "cp" or "mv" commands with "sudo" to copy or move files as root.  If you want to do things graphically, you can type "gksudo nautilus" to open nautilus as root.  You should be very, very careful using nautilus as root, as you can seriously frak up your system if you accidentally delete or move the wrong files.  (Fortunately, nautilus has a trash feature, so in that respect it's somewhat safer than using "sudo rm" from the terminal to delete files as root.)

If a package failed to install correctly, you probably got an error message telling you to run the command "dpkg --reconfigure -a" (though you may have ignored it at the time).  This command should also be preceded by "sudo".  Run that, then "sudo apt-get update".  This should fix your problem with Update Manager.

---

