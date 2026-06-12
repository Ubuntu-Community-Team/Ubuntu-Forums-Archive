---
title: "WM independent of GNOME?"
date: 2008-10-20
forum: Desktop Environments
---

### Post by 000krf on 2008-10-20
Hello all,

I've tried searching, but couldn't find exactly what I'm wanting to do. 

I have just completed a clean install of Ubuntu 8.04 on my Toshiba Laptop. What I would like to do is keep GNOME for system configuration, as the GUI tools seem to make it very user friendly, but use a lighter weight WM -one of the *boxes?- for my normal day to day computing. Is it possible to have both on the same computer but have them sort of independent of each other? I don't want icons on the desktop, with maybe the exception of mounted removable media. I also don't really want, but could live with panels. I also want to be able to access the applications listed in the GNOME menu via whatever menu system the WM uses. I tried using openbox inside GNOME in a previous install, but couldn't get the right-click openbox menu to show up. 

Is what I'm asking possible and relatively easy? Would it be best to set up two user accounts -one a sort of admin using GNOME, the other my "user" account using the window manager?

Thanks.

---

### Post by derouge on 2008-10-20
From the GDM screen you should be able to select just an Openbox session. There is also the option Openbox/Gnome which is what (it sounds like, at least) you seemed to have tried. Running just the Openbox session shouldn't autostart anything besides the window manager itself; unless, of course, Ubuntu has modified the autostart.sh files.

---

### Post by benerivo on 2008-10-20
You could try lxde, which uses openbox but comes with some extra applications such as a file manager, text editor, etc, rather than relying on nautilus and gedit. I'm not sure if it's available for 8.04, but the package is listed (and described) [here]("http://packages.ubuntu.com/intrepid/lxde") for intrepid ibex.

---

### Post by kerry_s on 2008-10-20
yes and no

you can use the gnome things, but if you go back to gnome the changes carry over. there are many ways/programs to make using a wm just as easy and if you know what you want you only have to do it once. linux is as much about learning and learning the different ways of doing things.

like for instance the menus in wm's can be done automatically with "sudo update-menus" and looks and stuff are basically a few lines in a text file. i use jwm which has all its settings in 1 file, but can use several if i want to get complicated.

---

### Post by 000krf on 2008-10-21
Thanks for the replies. I guess I'll play with things a little more. Now for another question... If I decided to remove GNOME, would my network and printers be affected since they were configured within GNOME?

---

