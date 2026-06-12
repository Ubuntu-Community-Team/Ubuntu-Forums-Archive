---
title: "question(s?) about the k7 kernel"
date: 2005-12-10
forum: Desktop Environments
---

### Post by ren wins on 2005-12-10
i have an amd athalon 2200, and i'm (TRYING TO) currently running the 386 kernel
i've heard about the k7 kernel... but i dont know anything about it
like, for example, i used to use SuSE, and i remember a few packages i tried to download made me choose btwn 386 or 686 or source package or something
if i change my kernel to the k7, will i have to compile everything myself?
is there a way to have both kernels installed? i've heard that you can have kde and gnome installed, and you just switch btwn the 2 at the login screen, can i do the same with 386 and k7?
could the k7 kernel make my computer work faster? better? stronger (we have the technology... chk chk chk chk chk chk chk...) or could it result in dozens of crashes and a 4th reinstall for me?

thanks in advance

---

### Post by Leif on 2005-12-10
[QUOTE=ren wins]
if i change my kernel to the k7, will i have to compile everything myself?[/QUOTE]

no

[QUOTE=ren wins]
is there a way to have both kernels installed? i've heard that you can have kde and gnome installed, and you just switch btwn the 2 at the login screen, can i do the same with 386 and k7?
[/QUOTE]

yes. both options will be available in grub.

[QUOTE=ren wins]
could the k7 kernel make my computer work faster? better? stronger[/QUOTE]

yes

[QUOTE=ren wins]
 could it result in dozens of crashes and a 4th reinstall for me?
[/QUOTE]
very unlikely. I use it, and it's been nice & stable, and I don't remember anyone complaining about it here at the forums either. anyway, you can keep the 386 kernel and remove the k7 if you need to.

---

### Post by patrickfromspain on 2005-12-10
if you want to try the k7 kernel it's so easy as opening a terminal an writing:

sudo apt-get install linux-k7

You won't have to compile anything... you will be able to continue as you had the 386 kernel. Using synaptic and apt-get the same way. Depending on how you installed the nvidia drivers you'll have to reinstall them, and maybe few other things (in my case, everytime I install a new kernel I'll have to reconfigure vmware, running a simple command). But all apps as openoffice, amarok, firefox, etc etc will continue to work as they did with the 386 kernel, but maybe faster.

When you install the new kernel, the new kernel will automaticaly show up in grub as the default one.

K7 could make your computer faster.. it probably will do. 386 is very generic, and k7 should take profit of special k7 features.

Also, don't uninstall the 386 kernel.. just in case something doesn't work as expected.

Hope it helps.

PD: I've been using the k7 kernel since I installed ubuntu a couple of months ago with no problems.

---

### Post by ren wins on 2005-12-10
awesome
now i just need to figure out my problem with /lib/modules ([http://www.ubuntuforums.org/showthread.php?t=101719](http://www.ubuntuforums.org/showthread.php?t=101719))

and hopefully ndiswrapper
and then i'll have an internet connection
and i can install the k7 kernel
and HOPEFULLY I CAN START USING MY COMPUTER FOR SOMETHING OTHER THAN TARGET PRACTICE AGAIN

---

