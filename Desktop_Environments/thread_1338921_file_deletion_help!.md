---
title: "file deletion help!"
date: 2009-11-27
forum: Desktop Environments
---

### Post by phillychease on 2009-11-27
i have a file in /opt and i cant delete it. 
there is no option saying to move to trash
and if i physically move it to the trash nothing happens.
how do i delete the file??

thanks! :D:D

---

### Post by SmittyJensen on 2009-11-27
> **phillychease said:**
> i have a file in /opt and i cant delete it. 
there is no option saying to move to trash
and if i physically move it to the trash nothing happens.
how do i delete the file??

thanks! :D:D
You need administrator privileges.

Try running:

```
gksudo nautilus
```

in a terminal and then delete the file from there.

---

### Post by chinmaya_n on 2009-11-27
You just have privileges under /home/<username> only !
Though you are the only user in your system, the root user i.e super user or admin is locked for security purposes.....
But you can always run your admin tasks using **gksu** or **gksudo** or **sudo** using before your command!

And sudo just works in terminal as it is a command line utility!
gksu and gksudo are GUI utilities ..... You can test to know the difference :popcorn:

Yaa.. Nautilus is the file manager in UBUNTU! You can always run admin tasks through GUI by doing as **SmittyJensen** said !

---

### Post by phillychease on 2009-11-27
[COLOR=Black]thank you SmittyJensen! it works :)
[/COLOR] 				 				[COLOR=Black]
[/COLOR]

---

