---
title: "Can't boot, init-functions messed up!"
date: 2005-12-08
forum: General Help
---

### Post by Sethiano on 2005-12-08
Hi!

While I was editning the *".../lsb/init-functions"* file I forgot the last *'}'* at the end of the file. Therefor I can't boot into Ubuntu GUI. When the Ubuntu bootscreen flashes and the system files are reed I get the message "syntax error" (no shit).

The problem is that when I start in rescue-mode and try to edit the file by using "vi/vim" I can't make any changes to it, because the file is Read-Only, eventhough I am logged on as Root. I tried to change the ownership to root by the "chown" command, but without sucess.

What the hell am I supposed to do?

I really, really don't want to reinstall my whole system due to this tiny little misstake.

Any help will be highly appreciated!

---

### Post by 23meg on 2005-12-08
[QUOTE=Sethiano]I get the message "syntax error" (no shit).[/quote]That reminded you of a C64, I bet :cool: 
[QUOTE=Sethiano]
The problem is that when I start in rescue-mode and try to edit the file by using "vi/vim" I can't make any changes to it, because the file is Read-Only, eventhough I am logged on as Root. I tried to change the ownership to root by the "chown" command, but without sucess.
[/QUOTE]
What exactly is the chown command you used, and what error did you get? Try "chown root:root FILENAME"

---

### Post by Sethiano on 2005-12-09
Have tried that, does'nt work!

One strange thing is that at first when I'll get the "syntax error in /lib/lsb/init-functions" I'll give my root password and become log on as root.

root@...

BUT, when I tries to open up init-functions with vim, nothing happends.
BUT (again), after I give the "su" command I am able to open the file with vim. :???: 

Help :confused:!

P.S Is it not possible to repair the file, by doing a "repair install" or something like that?
I have search and tried all diffrent commands with the live CD and all that, but whithout sucesss.

---

