---
title: "Desktop link straight to XP with Virtualbox?"
date: 2009-01-25
forum: General Help
---

### Post by Dark_Ronius on 2009-01-25
Hi there

I am running Windows XP with much success under Ubuntu (and actually faster than running it natively!!), and was wondering if it was possible to have a link on the desktop that would boot me straight into XP with Virtualbox, without having to choose "Virtualbox OSE" in the menu and start it from there?

It's mainly for my girlfriend to watch Jeremy Kyle and other daytime tv shows she misses now she's working on itvplayer, as moonlight support doesn't extend to the version of silverlight itvplayer needs (yet).

Also I would rather not install a firewall or anti-virus or anything like that on the xp virtual machine, and I'm not too fussed about security, as long as I can be sure it is basically running in a "sandbox" that won't affect the Ubuntu installation? My router has a firewall anyway, and I'd rather keep the impressive speed of XP in Ubuntu ;)

Thanks in advance

---

### Post by olskar on 2009-01-25
I think I can help you with your first question at least.

A link to:

VBoxManage startvm NameOfVirtualMachine

On the desktop should start it directly :)

And if you like me have space in the VM-name you got to write for example:
VBoxManage startvm Windows\ XP

---

### Post by Dark_Ronius on 2009-01-25
Hey thanks a lot for your friendly advice :D it works fine!

Take care

---

