---
title: "problem in compiz"
date: 2006-07-27
forum: Desktop Environments
---

### Post by firebolt77 on 2006-07-27
I am having a problem on setting up the compiz.
I followed the tutorial from dave hayes blog([http://www.davehayes.org/2006/05/22/howto-xgl-and-compiz-on-ubuntu-dapper-new-and-improved/]("http://www.davehayes.org/2006/05/22/howto-xgl-and-compiz-on-ubuntu-dapper-new-and-improved/")
I installed the packages manually(by downloading the packages and its dependecy packages from packages.ubuntu.com,not by sudo apt-get install).
After I installed the packages n setting up some files(such as startglx and startcompiz), I restart my computer, and then in the terminal I typed startcompiz(steps written in dave hayes tutorial).
The problem is when I typed startcompiz, it generates error like this:

[I]gnome-window-decorator:no process killed
compiz.real:mo composite extension
gnome-window-decorator,failed to load shadow images[/I]

can anyone help me to solve the errors?
any answer would be appriciated
thx

---

### Post by rafalr on 2006-08-08
Hi,

Last night I got exactly the same problem (Nvidia + Dapper + Gnome)

------
gnome-window-decorator, Failed to load shadow images
rafal@Ubuntu-AMD-64:~$ compiz.real: No composite extension
------

After some googling I found you need to do some more editing of your /etc/X11/xorg.conf, so that it contains:

------
Section "Extensions"
         Option  "Composite" "Enable"
EndSection
------

will try this evening so can not tell now if it works

you may also take a look at a very solid and simple guides at:
[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)
[https://help.ubuntu.com/community/CompositeManager/InstallingCompiz](https://help.ubuntu.com/community/CompositeManager/InstallingCompiz)

cheers,
rafal

---

