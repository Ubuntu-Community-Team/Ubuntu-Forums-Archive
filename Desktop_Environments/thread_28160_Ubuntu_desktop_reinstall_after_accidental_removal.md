---
title: "Ubuntu desktop reinstall after accidental removal"
date: 2005-04-19
forum: Desktop Environments
---

### Post by davegahan on 2005-04-19
Help ! While removing fonts from my system using synaptic I accidentaly removed my Ubuntu Desktop. I have a presentation to give and need a suggestion how I can from text mode with apt-get have my Ubuntu Gnome desktop back ?

---

### Post by heimo on 2005-04-19
This should do it (as root):
```
 apt-get install ubuntu-desktop
```

---

### Post by maqi on 2005-04-19
```
$ sudo apt-get install ubuntu-desktop
```

However, ubuntu-desktop is merely a metapackage which lists all the packages which make up the standard ubuntu desktop. 

It is not necessary to have this package installed as, of itself it does nothing apart from tell apt which packages to download to install the standard ubuntu desktop. The second you remove any package which is part of the standard desktop, eg totem, this package will be removed. But it really doesn't matter. And it certainly shouldn't break your desktop or your system.

Have you tried rebooting yet? I'm sure it will all be fine. Just in case,  write down the command above and run it from the console if GNOME doesn't come back up when you reboot.

regards,
maqi :)

P.S if you reinstall the ubuntu-desktop package it will automatically reinstall the fonts you removed. Like I say, you don't actually need it.

---

### Post by heimo on 2005-04-19
Yes, maqi is absolutely correct - good advice. You can have fully functional desktop without that specific package. You probably should first find out what you've messed and fix it a little more elegantly, but if that fails, option is to apt-get remove and then apt-get install that package and at least get back to where you started.

---

### Post by maqi on 2005-04-19
Yep, heimo is also correct :)

And please do let us know how it goes.

maqi

---

### Post by Jesus Franco on 2005-04-19
This IS NOT THE PLACE to ask for help. You people are making the staff do more work. Please read before posting.  ;-)

---

### Post by heimo on 2005-04-19
[QUOTE=Jesus Franco]This IS NOT THE PLACE to ask for help. You people are making the staff do more work. Please read before posting. ;)[/QUOTE]
 
Oops. You're correct. :-/ Should have noticed. I just pick up these in Unanswered Threads and sometimes fail to check which forum it's in. On behalf of people on this thread, sorry. 
 
No more posts in this thread, please. 
 
MODS feel free to delete / move.

---

