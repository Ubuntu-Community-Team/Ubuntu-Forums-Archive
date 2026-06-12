---
title: "Dist-upgrade"
date: 2005-09-16
forum: Desktop Environments
---

### Post by Nonno Bassotto on 2005-09-16
I'm not sure what a dist-upgrade exactly is, so I ask some questions before Breezy arrives.

1) I know Breezy has different repositories, so when we do the change we will have more programs and more updated. But I think there is something else. Am I wrong?
2) Can (should)  the dist-upgrade be made by Synaptic?
3) The new distro will have some new tools (SMEG, a graphical boot, maybe a working MIDI?). Since Hoary didn't have these things, I installed them, following the instructions in the present forum. Will the "native" Breezy installation be cleaner or in some ways better?
4) Should I take the system like it was at the beginning before dist-upgrading? I see many of the basic programs (evolution, OOo 1.4, ecc.) have a dependency on a package called ubuntu-desktop. This package is recommended for the transitions. If it is really so, I would have to reinstall a lot of things, and then remove them again. I don't know if this would be easier then starting from scratch.

Thank you
Andrea

---

### Post by John.Michael.Kane on 2005-09-16
[QUOTE=Nonno Bassotto]I'm not sure what a dist-upgrade exactly is, so I ask some questions before Breezy arrives.

1) I know Breezy has different repositories, so when we do the change we will have more programs and more updated. But I think there is something else. Am I wrong?
2) Can (should)  the dist-upgrade be made by Synaptic?
3) The new distro will have some new tools (SMEG, a graphical boot, maybe a working MIDI?). Since Hoary didn't have these things, I installed them, following the instructions in the present forum. Will the "native" Breezy installation be cleaner or in some ways better?
4) Should I take the system like it was at the beginning before dist-upgrading? I see many of the basic programs (evolution, OOo 1.4, ecc.) have a dependency on a package called ubuntu-desktop. This package is recommended for the transitions. If it is really so, I would have to reinstall a lot of things, and then remove them again. I don't know if this would be easier then starting from scratch.

Thank you
Andrea[/QUOTE]
 Yes it i will have diffrent repositories most of the soft ware there will be updated versions of what is used in 5.04..
yes you can upgrade using ubuntu update manager. however most here will tell you that your better off doing a clean install..
cleaner maybe since right now it's still a preview version, it's not know yet what the end outlook of the distro will be or feel.
in the endyou may want to do a clean intall. making sure most of your programs and hardware will work with the nex release. 

i hope this helps..

---

### Post by rplantz on 2005-09-17
[QUOTE=SD-Plissken]...however most here will tell you that your better off doing a clean install..
cleaner maybe since right now it's still a preview version, it's not know yet what the end outlook of the distro will be or feel.
in the endyou may want to do a clean intall. making sure most of your programs and hardware will work with the nex release. 
i hope this helps..[/QUOTE]

Can anyone describe the differences between a *distro-upgrade* and a *clean install*?

I'm running Hoary Hedgehog 5.04 AMD64-bit and looking forward to some of the 64-bit issues being resolved by a move to Breezy.

I'm fairly new to Linux sysadmin stuff, and I have several questions so I can be prepared when Breezy is released. (I know I'll want to upgrade right away.)

My machine is a single-user personal machine. No server issues, etc. I connect to the rest of the world through a wireless DSL link. (No cable, no copper DSL where I live.)

1. How clean is "clean"? Will it reinitialize my entire disk? I realize that I should back things up. I followed the Ubuntu defaults and don't have a separate partition for system stuff. Perhaps now would be a good time to partition my disk?

2. What are the specific differences between a clean install and an upgrade? I've seen several posts that say an upgrade to Breezy slows things down, but a clean install fixes that. Does this imply that some things don't get upgraded properly? If I upgrade, should I delete some things? Which things?

Can anyone can point me to a place where I can learn the differences? I'm willing to read source code if necessary to learn this stuff. (I'm good at C, C++, asm, and can figure out Java and scripts.)

Bob

---

### Post by Leif on 2005-09-17
A clean install refers to deleting the / partition and doing a new install. Many people keep /home on a separate partition, so their data and settings don't get deleted.

Please keep in mind that breezy isn't released yet. Yes, people doing upgrades are experiencing problems, but there's still a whole month where a lot of things can and will be fixed. If things are done right, there should be no reason for a clean install, and no difference from an upgrade (excepting, of course, random stuff you may have done in the meantime).

---

