---
title: "Mistaken multipackeg installetion removal"
date: 2005-04-10
forum: Desktop Environments
---

### Post by TheWizard on 2005-04-10
Hello,
I've just installed kubuntu,

by mistake I've installed "gstreamer0.8-plugins" and answared 'y' when asked, which installed like half of gnome.

I don't need it.
how do I know what was installed so I can remove it? I searched in vain  and found no logs or anything similar (I've also searched here and found nothing).

Thanks a bunch.

---

### Post by edubarr on 2005-04-10
You can check the dependency list for it if you use synaptic. Just select gstreamer0.8-plugins from the package list and eithre click on the properties icon on the bar or right click on it and select properties. A new dialog will show up and all you need to do is click on the dependency tab.

---

### Post by user-jon on 2005-04-10
synaptic also has a File --> History menu.. for what it installed/upgraded..

BUT you probably didn't use / don't have synaptic if you only installed Kubuntu.

you *can* also check the dependencies using  aptitude..

BUT since i'm a newbie to apt/dpkg myself.. does knowing the dependencies help?

i would *hope* it is the case that.. if you uninstall 'gstreamer0.8-plugins' itself..
then dpkg is smart enough to know nothing else is needing its remaining
dependencies and remove them too (that would solve the problem).

If not, I don't see how a non-expert can know which of its listed dependencies
are safe to remove.. and which were already there before the accidental
installation and therefore ought not to be removed??
(ie.packages 'recommended' or 'suggested' by other existing packages).


More-experienced comments please :)

---

