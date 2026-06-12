---
title: "Need gnome launcher help"
date: 2009-08-26
forum: Desktop Environments
---

### Post by rldev on 2009-08-26
I was hoping someone can help. After installing ATI Catalyst drivers, there is no menu access to the ATI Control Center. I have to run a terminal command to get it to pop up.

DISPLAY=:0 amdcccle

How can I create a launcher to get this command to run and launch the ati software?

---

### Post by enli on 2009-08-26
Right click on desktop > Create launcher. In the command field enter above command.

---

### Post by rldev on 2009-08-26
It doesn't work. I choose command line in the launcher, but I get an error when trying to launch it.

"There was an error creating the child process in the terminal."

I then removed the DISPLY portion and it seems to work.
amdcccle instead of "DISPLAY=:0 amdcccle"

Is there a way I can run this as root? It needs root to make certain changes.

Thanks.

---

### Post by enli on 2009-08-27
yes you can. In the launchers command field use
```
gksu amdcccle
```

---

### Post by rldev on 2009-08-27
It works. The strange part is, I was playing with gnomenu and those menus pick up the ATI software, but not mintMenu. I will leave that for a different post I suppose. Thanks so much.

---

