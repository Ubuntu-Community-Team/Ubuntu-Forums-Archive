---
title: "root/admin access for trash"
date: 2005-06-30
forum: Desktop Environments
---

### Post by Mais on 2005-06-30
I've recently run into a problem where I cannot empty the Gnome trash because I do not have access to a folder or file. Perhaps empty trash should be a root command? Yea I know it's a pain to enter a pass each time, but still....

--

Or, (I'm still new to Linux, so sorry if this all seems so obvious) is there a console command that I can use sudo with to empty that can? 

Thanks.

---

### Post by Leif on 2005-06-30
use gksudo nautilus. then go->trash, and empty.

---

### Post by Mais on 2005-06-30
[QUOTE=Leif]use gksudo nautilus. then go->trash, and empty.[/QUOTE]
Well this is odd. According to your steps those items are not in the trash, (which would explain why I can't delete them). However, they remain in the can in Gnome =\.


[If a mod wants to move this, it seems like it would fit more in a support forum now]

thanks for your help Leif

---

### Post by Leif on 2005-06-30
What do you get when you do "ls -al ~/.Trash" ?

---

### Post by Mais on 2005-07-08
[QUOTE=Leif]What do you get when you do "ls -al ~/.Trash" ?[/QUOTE]
 Ok, I figured out the problem.

When I used gksudo to open nautilus the only trash I could get to was a root-only trash. So anything in there didn't affect my user trash. So I Ctrl-Ced out of that and CDed to ~/.Trash and used sudo rm -rf *   Tada.

---

