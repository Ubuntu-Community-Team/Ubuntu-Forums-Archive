---
title: "Uninstall Unity 2D and Installing Unity 3D"
date: 2011-10-03
forum: Desktop Environments
---

### Post by suryateja.sun on 2011-10-03
Hai,

I recently found that I can install Unity 3D in my system and presently installed Unity 2D. What are the packages to uninstall 2D and install packages for 3D? Please name them. I tried it but after restart, there is no panel and needs to start LXDE and Gnome (I installed them) from Terminal.

---

### Post by dino99 on 2011-10-03
sudo synaptic:

- remove/purge ALL *unity* installed packages (select: status -> installed)
- install unity
(which is 3D)

close, log out, choose unity from lightdm logon
if you dont get what is expected, open a terminal & run: unity --reset

---

### Post by searchfgold6789 on 2011-10-03
In order to run Unity 3D, you have to:

[LIST]
[*]Have a good graphics card
[*]Have drivers installed for said good graphics card
[*]Have the correct session type (you can select which login type you want before you login, there's a menu for it at the bottom)
[/LIST]

---

### Post by ajgreeny on 2011-10-03
> **suryateja.sun said:**
> Hai,

I recently found that I can install Unity 3D in my system and presently installed Unity 2D. What are the packages to uninstall 2D and install packages for 3D? Please name them. I tried it but after restart, there is no panel and needs to start LXDE and Gnome (I installed them) from Terminal.
I assume you are running 11.04 natty, in which case you should not need to install unity3D, as it is included with the default installation.  However as searchfgold6789 has said, you need a fairly modern and up-to-date computer for the 3D version of unity to run.  I can not run it on my desktop computer even though it will run 10.04 with a fully compiz enabled desktop; the cube, wobbly windows, etc etc all run well, but unity -  not at all; it just reverts to the classic desktop in 11.04.

Mind you, I don't like unity, so I am not bothered about any of that.

If you uninstall unity 2D you may not be able to run a unity desktop of any kind, as I assume the 3D version is not working for you.  If that is the case, you do not really have much choice with your hardware, I'm afraid.

---

### Post by grahammechanical on 2011-10-03
I have both Unity 3D and Unity 2D installed on my 11.04 and my 11.10 installations. There is no conflict between the two. You will find that on 11.04 the fall back/low resolution mode boots into Unity 2D if it is installed.

In fact in 11.10 Unity 2D is the default fall back mode for machines unable to run Unity 3D. It is the default User Interface until a proprietary driver is installed that allows Unity 3D to run.

You can remove Unity 2D by using the Ubuntu Software Centre. Just search for it and select the four items and click Remove.

Regards.

---

