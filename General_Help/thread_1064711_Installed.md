---
title: "Installed??"
date: 2009-02-09
forum: General Help
---

### Post by Colo2 on 2009-02-09
Hey
Every time I install something, I dont know how to access it. For example
sudo apt-get install compiz. it said installed successfully but whenever I go to applications I cant find it anywhere.
Also VNC server, I installed that from a .rpm using alien, it says successfully installed but I cant find it anywhere!! :(

PLease help

---

### Post by howefield on 2009-02-09
Do you have Compizconfig Settings Manager in the System > Preferences menu ?

If not, install it with Synaptic and you will be able to load up and change the compiz settings.

What vnc program have you installed ?

---

### Post by Colo2 on 2009-02-09
thanks :P
TightVNC I downloaded it from their websites as .rpm format for Fedora and used alien to convert it to .deb. It said it worked fine but I dont seem to be able to access it.

---

### Post by Colo2 on 2009-02-09
Sorry for double post. Just to say theres no Compiz config in my system preferences

---

### Post by howefield on 2009-02-09
You can access it from the terminal, did you know that tightvnc was in the Ubuntu repository ? I mention it because it is usually best to install from the repository in order to get updates.

Remote desktop in your Applications > Internet menu also uses vnc.

---

### Post by howefield on 2009-02-09
> **Colo2 said:**
> Sorry for double post. Just to say theres no Compiz config in my system preferences

Install it with synaptic package manager. You are looking for compizconfig-settings-manager

---

### Post by Colo2 on 2009-02-09
thanks for your reply, Im installing compiz manager now. ALthough please note that for this pc, I need VNC SERVER not VNC Viewer! :P

Is that built in also? if so where can I find it?

---

### Post by ajgreeny on 2009-02-09
You seem to be doing things the hard way, Colo2!

Firstly, you should have had compiz already in ubuntu after installation, and you could have changed the general settings in *System > Preferences > Appearance*.  Confusing, I know, but compiz does not appear anywhere in your menus, it is there just as *Appearance*, or if you install Compizconfig-settings-manager there is the added *Advanced Desktop Effects Settings*.  I use hardy so those names may have changed slightly, but I think they are more or less the same, so have another look in your menus to see if they are there.

Secondly, why did you go to a fedora version?  You should have done a search in synaptic, which would have shown you that compiz was already installed.  I would suggest that you make synaptic your first port of call when looking for any software packages to install.  It is very rare that you can't find what you are looking for.

---

### Post by Colo2 on 2009-02-09
OK :P but it wasn't the compiz fedora, it was VNC which was fedora. The unix one was source code and I dont know how to build stuff from source code. :(

---

### Post by Colo2 on 2009-02-09
Umm, I found tightvncserver in synaptic, installed it and I am now at my original problem > Every time I install something, I dont know how to access it.

If I have to access it via terminal, how do I go about doing that?

thanks

---

### Post by Colo2 on 2009-02-09
All is well! :P thank you

---

