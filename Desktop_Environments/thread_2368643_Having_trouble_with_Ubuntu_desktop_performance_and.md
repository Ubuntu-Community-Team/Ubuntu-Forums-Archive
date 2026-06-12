---
title: "Having trouble with Ubuntu desktop performance and design..."
date: 2017-08-13
forum: Desktop Environments
---

### Post by dave_h2 on 2017-08-13
I'm trying to use Ubuntu on a newer laptop (like Intel i5 processor), an older laptop (like Core 2 Duo), and in VirtualBox (on a newer laptop), but the performance is just almost intolerable on anything but the newer laptop (non-VM), and I'm trying to get the window top-bars to look and behave more like Windows (as opposed to Mac).

I've tried following some manuals but the performance is so bad that I'm stuck. I've read that Ubuntu uses Unity, which needs like a massive 3-D card with tons of memory (I'm exaggerating), but I don't care to use 3-D effects when I'm just testing out Ubuntu and using it for testing out websites or programs for security reasons.

Can anyone recommend what they consider the best solutions here? I've been using versions 12 through 16 (I'm just trying out 16), but at this point I'm just considering using the LiveCD in an ISO file loaded into VirtualBox as a CD to see if that gives better performance and I don't have to worry about problem-causing changes that I may not be very familiar with in the session.

---

### Post by &amp;KyT$0P# on 2017-08-13
Xubuntu.  It's lighter weight and can be customised to be more like Windows.

---

### Post by Autodave on 2017-08-13
2 votes for Xubuntu.  It also uses much less resources.

What are the specs of all 3 machines? What video cards are they running? Have you installed any drivers for the video cards? If so, where did you get the drivers from?

---

### Post by BloodyIron on 2017-08-15
Unity uses compiz and your GPU to reduce the CPU cycles needed to draw your interface.

-In the Virtualbox instance it's going to run poor because I suspect you haven't setup 3D Acceleration within Virtualbox.
-In the core2duo instance, the GPU you have is probably just not up to the task.
-In the i5 instance it's likely using the intel GPU, hence it being acceptable.

As the others have mentioned, xubuntu will work very well for your needs as it sets you up with XFCE4 which is much more lightweight in regards to processing power for your GUI. But you don't need to reinstall Ubuntu to Xubuntu to get it!

One of the things I love about Ubuntu is the meta packages for the DEs (Desktop Environments). So what you can do is install the packages for XFCE4 on your current setup and just switch at the login prompt to XFCE4, without having to reinstall!

The docs page is at : [https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

So in your case I would recommend:

> apt-get install xubuntu-desktop

It will install a lot of packages. When it's done, log out, and there will be a menu in the top right (unsure which icon you will have), where you can select "Xubuntu Session" or it might be labelled "XFCE4 Session". Then when that's selected, just login, and you're in like flynn!

Enjoy ;^)

---

### Post by lammert-nijhof on 2017-08-15
I have Ubuntu 16.04 on a second generation i5 laptop and it loads in  less then 20 seconds, so please define what is intolerable performance  and for which programs. Maybe your disks are very slow, I use a modern  1TB SSHD. Maybe you expect too much from the poor 3D support of most  laptops with integrated graphics. My old 2-core AMD Turion laptop at  2.3GHz (RIP) from 2008 could not run HD YouTube video, but that is the  limitation of the older 2-core CPUs. It could run Ubuntu and it would  react within say 1-2 seconds.

Look for an Intel, AMD or Nvidea driver in "Software and Updates" tab "Additional drivers" to get the best 3D performance. In Virtualbox the 3D performance will be mediocre compared to the real video card.

You can't use the top bar to launch applications, in Ubuntu you use the launcher on the left and that works very good.
I  run Unity with Intel Integrated Graphics and I have no issue with  Ubuntu, it is very responsive, reacts in general in less than a second.
I can guarantee you that the live CD will be worse and you will have to redo all your changes after each boot.

You  could switch to another distro like Xubuntu, but your response times  will not be very different. Other distros use considerably less memory,  but do use the same Linux OS and codecs (translation software) to  display e.g. HD YouTube video or Games, so with respect to CPU load they have no big  advantages. 

If you want a Windows like interface, use Linux Mint  18.2 or Peppermint 8, but don't expect significant better response times  or lower CPU loads.

---

### Post by oldfred on 2017-08-16
My old laptop was core2 duo but now 10 years old. It only had 1.5GB of RAM.
I used Ubuntu, but when Unity came out it was too slow, so I installed flashback/fallback/gnome-panel. Essentially the same but somewhere it changed from gnome2 to gnome3, but was like the old Ubuntu with top & bottom panels. My Desktop has a 4:3 monitor & side panel of Unity took too much space also.

I did go back and update from 12.04 to 16.04 on old laptop and was surprised Unity was functional, only a bit slow. But I still use gnome-panel.

       [https://wiki.archlinux.org/index.php/GNOME/Flashback](https://wiki.archlinux.org/index.php/GNOME/Flashback)
The differences to the MATE project is that GNOME Flashback uses GTK+ 3 and tries to follow the current GNOME development by integrating recent changes of the GNOME libraries.
[https://wiki.gnome.org/Projects/GnomeFlashback](https://wiki.gnome.org/Projects/GnomeFlashback) 
   Xenial flashback w/metacity tweaks 
[https://wiki.gnome.org/Projects/GnomeFlashback](https://wiki.gnome.org/Projects/GnomeFlashback)
[http://ubuntuforums.org/showthread.php?t=2302432](http://ubuntuforums.org/showthread.php?t=2302432) 
   
kansasnoob on flashback
[http://ubuntuforums.org/showthread.php?t=2324120](http://ubuntuforums.org/showthread.php?t=2324120)
> Ubuntu GNOME offers a Classic session but it's not at all easily customized and runs on top of the mutter window manager which is much more resource hungry than either MATE's Marco WM or Flashbacks Metacity WM.
IMHO if someone knows they prefer the old school GNOME 2 experience they're better off just installing Ubuntu MATE because it acts and works just like GNOME 2 and includes a nifty MATE Tweak tool.

---

