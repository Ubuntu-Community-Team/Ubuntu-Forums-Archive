---
title: "Huge CPU usage in Gnome3 vs KDE &amp; Unity"
date: 2012-06-06
forum: Desktop Environments
---

### Post by sreejiraj on 2012-06-06
Hi,

this is something I have noticed over the last 4 months. This is true for all the distros I have tested - ubuntu, debian, OpenSuse and Fedora.

After Gnome went to version 3, my system (Core i3 first gen, 4 GB ram, ATI HD5650) runs very hot.

When I say very hot, i mean it gets so hot that it turns itself off.

When I use fglrx driver for my ATI card, it's better, but I can feel the heat on my palms.

Using radeon drivers, on moderate usage such as browsing, the temperature ranges between 72 and 80 degrees celcius.

Using fglrx, it is in the early 70s.

If I start watching youtube videos, and the system is using radeon drivers, it will hit the 88 degree threshold and force a shutdown.

If it's on fglrx, it will hit the 80-84 degree range.

This problem is there only when I use Gnome 3 shell. When I use KDE, it runs at about 65-66 degrees on normal usage and slightly more when I am watching video etc..

I am in India and the room temperature is in the early 30s these days.

Unity is also decent, though not quite as cool as KDE.

I know that fglrx has been installed properly etc.. I get about 1200 frames per second on fgl_glxgears (without maximizing the window.) The highest I've ever got is 1800 fps under Centos 6.

My hunch, after testing on fedora, suse etc, is that this is an issue with Gnome Shell or GTK 3 in general.  

There is also another 'bug'. When I got to Unity's system description, it says I am on a Vesa driver. Could this be the issue?

PS:when Gnome moved from 3.2 to 3.4, this improved slightly (about 30%). The experience is for gnome 3.4 on precise and f17.

---

### Post by R Clemons on 2012-06-08
I have the same graphics card(hybrid graphics so lots of problems) and I believe it's a known bug that Gnome Shell uses a ton of cpu power with the fglrx driver.  That's probably why it gets so hot.

If you have an integrated graphics card as well then that could be the bigger issue, but using a different desktop environment shouldn't fix that problem.

---

### Post by R Clemons on 2012-06-08
Didn't notice that you said you had an i3(I have a first gen i5 and HD5650).  I had to install with the alternate cd since my laptop overheated while trying to install using the live cd.  Ended up having to install the driver from ATI's website and switch to the intel graphics to get the temp under control.  I was also using gnome 3, but I ended up running into the same problem with Gnome Shell using too much CPU usage.

Did you really have no heat problems with KDE on a Linux 3.2 distro using the default drivers?

---

### Post by LacerdaPT on 2012-06-28
Hi.

Any updates/ideas?

This affects me too. I can provide information you need. (I have a i7 with a HD5000)

Cheers

---

