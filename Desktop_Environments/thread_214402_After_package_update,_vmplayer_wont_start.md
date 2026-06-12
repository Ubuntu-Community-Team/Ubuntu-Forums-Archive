---
title: "After package update, vmplayer wont start"
date: 2006-07-12
forum: Desktop Environments
---

### Post by howbag on 2006-07-12
Hey!
I am using Dapper Drake, and have been using vmwares "player" to run a windows xp installation because of a game I can't live without (ultima online), anyway, after I was notified by the yellow message in the upper right corner about some updates, I just selected every package and hit okey. It required a restart of the machine. fair enough, but now the errors starts to evolve; when I started gnome, I got a message telling that x server and gnome had different keyboard settings, and I should chose which I wanted to keep. I selected gnomes settings (which later seemed to be the right one), and chose not to see that message again.

[B]But the main error which irritates me, is that, when Im running vmplayer and select my windowsXP virtual machine file, vmware wont start because:

```
 Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded. 
```

I have searched, but only came up with spanish, french and italian linux sites writing something about it.

Anyone got the same problem or know how to solve it?
Thanks for replies![/B]

-DapperNewbie

---

### Post by bigken on 2006-07-12
hi ive had this prob i got round by running the vmware install again ;)

---

### Post by howbag on 2006-07-12
I get this after fresh install of vmplayer: [I]Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1[/I]

New install wasn't that constructive either :(
seems like its the same error.. the program is installed, but shows the same error as before.

---

### Post by reztho on 2006-07-12
Because of the new kernel, a new vmware player kernel module is needed. It seems than vmware team are slow to supply it... so if you need vmware player working now, apt-get the vmware player source module and compile it yourself.

---

### Post by howbag on 2006-07-12
Ouch, I'm lost with compiling :/ think I'll wait for the vmware team to do the work for me.

---

