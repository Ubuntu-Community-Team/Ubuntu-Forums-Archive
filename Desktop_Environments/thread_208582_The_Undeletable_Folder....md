---
title: "The Undeletable Folder..."
date: 2006-07-03
forum: Desktop Environments
---

### Post by SEMW on 2006-07-03
Hi, all.

OK, new Linux user here.

I've just sucessfully managed to sucessfully make a couple of NTFS partitions readable from within Ubuntu by following the instructions [here]("https://help.ubuntu.com/ubuntu/desktopguide/C/partitions-booting.html") and editing /etc/fstab.

I had two partitions I wanted to read, which Windows calls "Windows" and "Documents & data", so initially I named them accordingly (in /media/).  However, when I got to editing fstab, I was slightly worried that there were no separators between the different parts of an entry  - no comma or anything, just a space - so I wasn't sure whether it would work with a folder name with a space in it.  So just to be safe, I went back through the process using "documents" as the name of the folder; which worked fine.

But now I have an unused folder named "Documents & data" in /media/.  And this is the actual problem.  Well, it's not much of a problem since it's not actually doing any harm, but there surely must be a way to delete it.  Trouble is, I can't find it.

I can't delete it from the file manager, since the permissions are set to root only, and, as the properties window helpfully points out, "You are not the owner, so you can't change these permissions".  There's nowhere to use sudo or type in a password.

But when I try to use the terminal and use ```
sudo chmod 777 /media/Documents & data
``` to change the permissions, it gives me "data: command not found" -- it doesn't recognise the space as part of the file name.

A sentence [here]("http://www.linux.com/howtos/Secure-Programs-HOWTO/file-names.shtml") seems to suggest double-quotes around the file will work, but although the terminal seems to accept it, the permissions don't change.

So how d'you do it?

(By the way, whilst I'm posting in Desktop support, is there any way to make pressing the middle button down work as Universal Scroll instead of paste, especially in Opera?  Makes browsing long forum threads so much easier...)

---

### Post by lazyd2 on 2006-07-03
Why don't you just type
```
gksudo nautilus
```
give your root password, go to the directory you want and delete the empty file?

---

### Post by meng on 2006-07-03
a folder called Documents & data would need to be entered as Documents\ \&\ data in shell.

---

### Post by SEMW on 2006-07-03
> **lazyd2]Why don't you just type
"gksudo nautilus"
give your root password, go to the directory you want and delete the empty file?[/QUOTE]
Mainly because I'd only been using Linux for a day or so now and didn't know that was possible... :) 

Excellent said:**
> Grandma test[/URL].  It's excellent if everything works perfectly first time, but if it doesn't, the learning curve isn't un-steep -- less than a day after I first installed Linux, I'm already posting questions that include statements like "But when I try to use the terminal and use "sudo chmod 777""...

[quote]
a folder called Documents & data would need to be entered as Documents\ \&\ data in shell.
Thanks; I'll remember that in future -- though for the time being I think I'll play it safe and stick to single word lowercase names ;)

Many thanks, all.

---

### Post by meng on 2006-07-03
Other tip: type "sudo chmod 777 /media/Docum"
and then press TAB for autocompletion.

---

