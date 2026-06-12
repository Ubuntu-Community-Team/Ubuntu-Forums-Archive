---
title: "How To Stop GUI from loading at Startup?"
date: 2008-02-12
forum: Desktop Environments
---

### Post by matey3 on 2008-02-12
I know I read where everyone said to edit inittab, but I searched the whole file system and there are no inittab file any place (not under /etc either)??

Is there any other file I should look into for the stuff that load at the start up?
I have problems with xdm, gdm and kdm. I do get the login on them but then I get a blank page with a commandline on top left and can not access ttyX by cntrl and/or alt F1~ F6 etc.? (cant access anything else??)

I can su then use ps -A to kill some of the processes to get back out of the X env. but that is no good. 
I'd like my ubuntu feisty 7 stop loading gui at startup (as it shouldnt any way) ...


many thanks in advance!

---

### Post by njparton on 2008-02-12
In the gnome menus (under administration I think) there's an option to configure services. Untick "gdm" and it will stop immediately, returning you to a command prompt and will not restart automatically on reboot.

No need to mess around with scripts, it's as simple as that.

---

### Post by kpkeerthi on 2008-02-12
System -> Administration -> Services

---

