---
title: "Please! How to install a runnable fluxbox from a pure &quot;TEXT&quot; ubuntu"
date: 2007-02-17
forum: Desktop Environments
---

### Post by anguste on 2007-02-17
Hello all

I've installed a "text" (terminal only) ubuntu 6.10

The other day I wanted to try fluxbox.. then..

I've apt-get the "gdm" and "fluxbox", but after reboot it reports "can not find /etc/X11/X".

What's the function of that file? I don't know how to deal with this, is there any other package I should install?

Thanks in advance for your time and kind help!

---

### Post by yabbadabbadont on 2007-02-17
If you haven't already got it installed, install x-window-system-core.

---

### Post by anguste on 2007-02-17
thanks for reply

now the message changes to "can not start X server due to some internal problems", is there any settings I can change?

---

### Post by damvcoool on 2007-02-17
personal experience:

when i installed fluxbox from the server install i installed xserver-xorg fluxbox and nothing more it worked just fine
```

sudo apt-get xserver-xorg fluxbox

```

---

### Post by anguste on 2007-02-17
> **damvcoool said:**
> personal experience:

when i installed fluxbox from the server install i installed xserver-xorg fluxbox and nothing more it worked just fine
```

sudo apt-get xserver-xorg fluxbox

```

may I ask what display card you are using? I have an old nvidia mx440.. does it require any special drivers?

---

### Post by kerry_s on 2007-02-17
Here's the way i do it->

server/command-line install(depends what .iso you use)(i use-> [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso))
login
sudo su
nano /etc/apt/sources.list
comment(#) out cdrom and deb-src, uncomment all deb repos
ctrl and x and y and enter to save
apt-get update
apt-get install x-window-system-core gdm fluxbox synaptic

For nvidia->
apt-get install nvidia-glx
nano /etc/X11/xorg.conf
change 
    Driver         "vesa" or it might say "nv"
to
    Driver         "nvidia"

type> reboot
select fluxbox in option>session and login


The reason i think yours is screwed up is because you installed in the wrong order, as you installed fluxbox with out X, same with gdm, so they had no X to set up/configure.

---

### Post by anguste on 2007-02-17
> **kerry_s said:**
> 

The reason i think yours is screwed up is because you installed in the wrong order, as you installed fluxbox with out X, same with gdm, so they had no X to set up/configure.

Thanks and I guess so now.

Is there any way to remove all the packages completely (incl. settings & configurations) so that I can install them in the RIGHT order?

---

