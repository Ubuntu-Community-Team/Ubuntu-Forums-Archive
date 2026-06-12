---
title: "Adding LXDE Desktop to obsolete Xubuntu system?"
date: 2011-10-07
forum: Desktop Environments
---

### Post by fugazi32 on 2011-10-07
Hi guys,

I'm quite familiar with Lubuntu 11.04 but would like to add LXDE to my old Xubuntu 8.10 box (which I need to keep as 8.10 to keep various applications I use running properly!)

Any tips? New repositories? Compile from source?

Many thanks,
Nathan

---

### Post by kemtnbkr on 2011-10-08
Hi, I just installed lxde on my 11.04 recently, as I have an older comp that can't really handle Unity very well.  Plus I like the general feel of lxde, too.  

But more to the point, I didn't have to mess with adding repositories or anything, the package installed fine.  I'm not an expert at all, but I think you'd be fine with just a basic install- it uses the Openbox DE with a panel (and wallpaper) 'on top', effectively.  Your older distro should support it just fine, I think.

LXDE cut down my RAM usage a somewhat appreciable amount; I get more use out of the basic layout than anything else, really.

Hope I answered your question somewhat.  Only thing I have to complain about is it automatically brings in LXDE's file manager, terminal emulator, and text editor (plus I'm sure something else too).  I still prefer nautilus/gedit to the included File Manager and Leafpad, but they both work fine too, its nothing more than preferring not to change.

---

### Post by fugazi32 on 2011-10-19
Cheers, will give it a go.

Did you use *sudo apt-get* to install?

---

### Post by mcduck on 2011-10-19
Your biggest problem would be that 8.10 reached it's end-of-life year and a half ago, meaning that it's software repositories are already closed and it's rather unlikely that you'd be able to find any repository providing extra packages for it.

Compiling from source *might* work, but even that will quite likely require more up-to-date package versions than what you have available.

I would seriously suggest trying to find a way to get your applications to run on some later version of Ubuntu, using a version that's out of support means you'll have serious problems getting any software, and in addition you aren't getting any security updates for the machine which *is* a big deal if it's connected to the Internet.

---

