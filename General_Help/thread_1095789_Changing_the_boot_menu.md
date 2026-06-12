---
title: "Changing the boot menu"
date: 2009-03-14
forum: General Help
---

### Post by Mohammad Ansarin on 2009-03-14
hello everyone.

so uh... I want to know how I can switch the default in the boot menu of ubuntu (GRUB) to Windows Vista. I remember doing it a few years back but I don't remember how I did it. Also another question: every time I update ubuntu, 2 new options come in that menu, how can I remove the extra options that load up the old not updated ubuntu? And also please mention how I can change the time before the default starts.

sorry guys, half-newbie here!:)

byebye

---

### Post by Admiral Yi on 2009-03-14
Go to system>administration>start up manager. You will need to enter your password. In the first screen you will see a drop down box above which it says 'default operation system' click on the box and change it to windows vista. I don't know how to remove the other options, but i'd keep them there as they are useful if something goes wrong.

---

### Post by jayanramesh on 2009-03-14
First if you don't see start up manager at system administration go and add from APPLICATION>ADD/REMOVE and click system tools and select startup manager to add

---

### Post by OrangeCrate on 2009-03-14
If it's not listed in Add/Remove, you'll find startup manager in Synaptic.

---

### Post by zvacet on 2009-03-14
New options in grub are new kernel and recovery mode of same kernel.It is good choice to have two kernels just in case that something goes wrong with one you can boot in second.if you have more then two kernels installed then in synaptic type linux-image and you will see list of installed kernels.From that list uninstall kernel with lower number.

---

### Post by mainshell on 2009-03-14
I was working on this too. Thanks for the above advice - all of which I have used. This method is better than editing the grub configuration file /boot/grub/menu.lst, as alluded to in [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

