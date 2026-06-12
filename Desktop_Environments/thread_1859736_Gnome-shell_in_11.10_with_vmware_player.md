---
title: "Gnome-shell in 11.10 with vmware player"
date: 2011-10-14
forum: Desktop Environments
---

### Post by psikobare on 2011-10-14
hi

before moving to oneiric with gnome-shell i decided to try it a few days/weeks in a virtual machine in order to learn and get use to it
i use vmware player for its performance (tried virtualbox, with no success), version 4.0.0 build-471780 in win7 64bit

installation (desktop amd64) is fine

moving to gnome-shell seemed pretty easy according to tutorials

apt-get install gnome-shell

logged out, log back in in GNOME

but i appear to always end up using the fallback (GNOME and gnome classic look the same)
screenshot, loging with GNOME:
[[IMG]http://uppix.net/3/4/6/19f4b19ed80e4b3e8e8ef4bb5d971t.jpg[/IMG]]("http://uppix.net/3/4/6/19f4b19ed80e4b3e8e8ef4bb5d971.html")

3d acceleraton is activated in vmware

[COLOR=Black]glxinfo [COLOR=#000000]**|**[/COLOR] grep [/COLOR][COLOR=#FF0000][COLOR=Black]"direct rendering"
gives me [/COLOR][/COLOR]direct rendering: Yes

but gnome-shell --replace
gives me:
failed to create drawable
(gnome-shell:1487): clutter critical, unable to initialize clutter, unable to select the newly created GLX context
window manager error: unable to initialize clutter


has someone manage to use gnome-shell in a virtual machine?

---

### Post by 1beb on 2011-10-14
bump. Same problem here.

---

### Post by Lexas on 2011-10-15
Same here!

---

### Post by Lexas on 2011-10-15
Hello, I just mannaged to get gnome3 running, Try installing Ironhide ([https://launchpad.net/~mj-casalogic/+archive/ironhide/]("https://launchpad.net/%7Emj-casalogic/+archive/ironhide/")) from this PPA
 **ppa:mj-casalogic/ironhide**. 

Then reinstall nvidia-current and write the command:

```
 sudo ironhide-configuration
```Once you've finished the configuration, reboot your PC and try to get in gnome3, you shouldn't fallback.

If you need to run an application that requires 3d acceleration, install ironhide UI and check those programs, or run 
```
optirun your-program
```to definitely enable/disable 3d acceleration write respectively:
```
sudo ironhide-enablecard
``````
sudo ironhide-disablecard
```

---

### Post by psikobare on 2011-10-17
> **Lexas said:**
> Then reinstall nvidia-current
i'm curious about that part

??

let me be clear, i want:

host OS: win7 64bit
guest OS: Ubuntu 11.10 with gnome-shell environment

---

### Post by e79 on 2011-10-17
Another alternative would be to download and install VirtualBox. I was successful in testing Unity and Gnome3 GUI inside it whereas VMware was unable to do so (make sure to install the Guest Additions).

Just my $0.02

---

### Post by Lexas on 2011-10-17
> **psikobare said:**
> 
let me be clear, i want:

host OS: win7 64bit
guest OS: Ubuntu 11.10 with gnome-shell environment

That error message you got is because your display is not being correctly detected, mostly because you have an optimus graphics card system, you can choose between installing ironhide in ubuntu or, if your virtual machine lets you, setting your virtual machine to detect only an intel graphics card.

---

### Post by psikobare on 2011-10-18
> **Lexas said:**
> you can choose between installing ironhide in ubuntu
that would be ubuntu as a host OS, or am i wrong?

anyway, i have a ATI HD4850, not quite optimus

---

### Post by makitso on 2011-10-18
I have been running 11.10 in Virtualbox since Beta 1.  I also have the Gnome 3 shell installed.  Gnome 3 works with full 3d support.  However, periodically, it fails after an update and although I can pick gnome from the login in screen its is really in fall back mode. 

The latest update (last few days?) caused this to happen again.  So, I rebuild a release in VB again and did all my things only to see that yes, it now falls back.:(

And yes, if I log into Unity it is full 3d

---

### Post by psikobare on 2011-10-18
i managed to install everything in virtualbox

however it's very instable when in fullscreen, and unperfect when windowed

---

