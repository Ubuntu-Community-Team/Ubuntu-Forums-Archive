---
title: "removing/uninstalling files"
date: 2005-12-08
forum: General Help
---

### Post by twigboy on 2005-12-08
Hi
I was wondering how to unistall programs.  Like say I wanted to get rid of a theme do I just delete its file or do I need to run a command in the shell?
thanx

---

### Post by aysiu on 2005-12-09
How you *un*install a file depends greatly on how you installed the file and what kind of file it is.

Can you be more specific about what you installed and how?

---

### Post by twigboy on 2005-12-09
well say i installed the file with synaptic. how would i unistall those files?
also for uninstalling themes i just drug them to the theme folder and installed them through theme prefrences.  how would i uninstall those?

---

### Post by aysiu on 2005-12-09
[QUOTE=twigboy]well say i installed the file with synaptic. how would i unistall those files?[/quote] Through Synaptic. Right-click, mark for removal, apply. > also for uninstalling themes i just drug them to the theme folder and installed them through theme prefrences.  how would i uninstall those? Go to /home/twigboy/.icons and delete the folder of the theme you don't want any more.

---

### Post by twigboy on 2005-12-09
huh its so easy.  thanx aysiu.
oh yea.  there are no registry entries or any other files that need to be uninstalled like in windows?
also how would i uninstall programs that i would need to first compile?

---

### Post by aysiu on 2005-12-09
[QUOTE=twigboy]huh its so easy.  thanx aysiu.
oh yea.  there are no registry entries or any other files that need to be uninstalled like in windows?[/quote] No. If you want to, you can mark applications for *complete* removal in Synaptic--that removes the application's configuration files as well. > also how would i uninstall programs that i would need to first compile? I don't remember.

---

### Post by RAOF on 2005-12-09
[QUOTE=twigboy]...also how would i uninstall programs that i would need to first compile?[/QUOTE]
There you're left to the mercy of the people who wrote the makefile.  Some programs are nice, and have a "make uninstall" target that will uninstall something that you've installed with "make install", if you've still got the source code directory lying around.

Better, though, is to use the amazing "checkinstall" program - rather than running "sudo make install" as the final part of installing something from source, you run "sudo checkinstall" and it builds & installs a .deb of the program, so you can now use synaptic to remove it.  Yay!  (You can find the checkinstall package in the universe repository)

---

