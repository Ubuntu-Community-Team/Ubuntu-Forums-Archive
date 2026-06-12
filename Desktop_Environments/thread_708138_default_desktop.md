---
title: "default desktop"
date: 2008-02-26
forum: Desktop Environments
---

### Post by RJ Hythloday on 2008-02-26
[SIZE=2]So I've searched and can't find the answer to this.

I installed edubuntu because I want the apps that come installed in it, but I wan't fluxbox for the desktop mgr. It's for a kids pc w/ 900mhz 512 ram.

I've installed xdm for the display mgr.

I've tried rebooting and restarting x but I've not seen an option to choose a window mgr.I think that because of having xdm for the default mgr I don't have an option at login to choose the desktop. Is there another way to choose the default desktop?
[/SIZE]
[SIZE=2]I installed fluxbox from terminal, and in synaptic I installed the edubuntu light (xfce) desktop and removed the edubuntu desktop. I haven't seen any difference I think it's still the same.[/SIZE]
 
[SIZE=2]Also after I switched from gdm to xdm I lost the option to shut down. It offers restart, hybernate, standby etc but shutdown is not there.

tia for any help.

Bob[/SIZE]


---

### Post by RJ Hythloday on 2008-02-29
^^ bumpida bumpida
 
Anyone?

---

### Post by kerry_s on 2008-02-29
your going about it all wrong.

don't use xdm, stick with gdm.

just install fluxbox(sudo apt-get install fluxbox)

than log out of xfce4, choose fluxbox from the gdm menu and log in.

welcome to fluxbox.

ps: fluxbox is not really kid friendly, xfce4 would be easier. you'll have to do a bit of configuring to make fluxbox kid click friendly.

---

### Post by kerry_s on 2008-02-29
you know you don't have to use a certain distro just to get a few software, they all use the same repo. just jot down what you like in edubuntu and install them using synaptic.
so for instance fluxbox is what your after grab fluxbuntu and then just install the extra packages you want.
[http://releases.fluxbuntu.org/7.10/rc/](http://releases.fluxbuntu.org/7.10/rc/)

fluxbuntu is you guessed it the fluxbox version of ubuntu, it will save you alot of setup time.

your specs are good enough, you should be able to run what ever you want.

anyways, i use a debian custom install on 450mhz 256ram and in debian you can also get them separately(ubuntu is based on debian)

see pic, to get what i mean.

---

### Post by RJ Hythloday on 2008-03-04
> **kerry_s said:**
> you know you don't have to use a certain distro just to get a few software, they all use the same repo. just jot down what you like in edubuntu and install them using synaptic.
so for instance fluxbox is what your after grab fluxbuntu and then just install the extra packages you want.
[http://releases.fluxbuntu.org/7.10/rc/](http://releases.fluxbuntu.org/7.10/rc/)
 
fluxbuntu is you guessed it the fluxbox version of ubuntu, it will save you alot of setup time.
 
your specs are good enough, you should be able to run what ever you want.
 
anyways, i use a debian custom install on 450mhz 256ram and in debian you can also get them separately(ubuntu is based on debian)
 
see pic, to get what i mean.
 
Yeah, I've looked at fluxbuntu but it just doesn't seem like any development is going on there. Since I got 2x256 I think I'll be using edubuntu w/ the xfce desktop.

---

