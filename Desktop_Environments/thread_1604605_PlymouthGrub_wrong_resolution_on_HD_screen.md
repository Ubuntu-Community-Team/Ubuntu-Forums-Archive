---
title: "Plymouth/Grub: wrong resolution on HD screen"
date: 2010-10-24
forum: Desktop Environments
---

### Post by mr32 on 2010-10-24
Hello,

I've got a HD screen: 1920x1080p. Grub (1.98 ) has the resolution: 800x600 and Plymouth also. It is irritating me that plymouth shows a very ugly purple splash screen in a very low resolution (800x600). How can I fix that? 
I've got an ATI Radeon HD 4670, and use the drivers from ATI...

mr32 :cool:

---

### Post by dougalkerr on 2010-10-24
Do away with the ATi drivers first and see what happens.
I have the HD 3450 card in my Dell laptop and some times it works better without the ATi drivers.
I also have a 1900 x 1080 screen res and the spalsh screen is very pleasing on both my Ubuntu and my Ultimate Edition installations.

---

### Post by mr32 on 2010-10-24
But, can I play my favourite games without ATI's 3d acceleration? Or do I have to choose between gaming and a nice splash screen?

---

### Post by dougalkerr on 2010-11-07
Sorry a small correction to my last post - my screen res is actually 1900 x 1200.

I also use Ultimate Edition 2.8 nowadays for most of what I do. I still use Ubuntu 10.10 which UE is based upon but, only for the odd small thing. Ultimate Edition also has a 'Gamers' Edition so, I would assume that all the codecs and a lot of drivers are up-to-date for playing games.
Check out Ultimate Edition Gamers Edition on their website.
It is a big file to download as you would expect but, it sounds like the people that want to use Linux for games will use this edition.
Good luck and happy gaming.

---

### Post by mister_playboy on 2010-11-09
> **mr32 said:**
> Or do I have to choose between gaming and a nice splash screen?

I think you do have to choose between the two.  Getting the full resolution at boot requires something called kernel mode setting (KMS) and it is not available when using proprietary drivers from nVidia or ATi.

---

### Post by speedwell68 on 2010-11-09
I had this problem when using the proprietary Nvidia drivers.  The solution I found was to install the 'Startup Manager' in Synaptic and then configure the startup resolution from there.

---

### Post by mkeyes001 on 2010-11-10
this will fix it....

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by bigsmitty64 on 2010-11-10
> **mkeyes001 said:**
> this will fix it....

[http://news.softpedia.com/news/how-to-fix-the-big-and-ugly-plymouth-logo-in-ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/how-to-fix-the-big-and-ugly-plymouth-logo-in-ubuntu-10-04-140810.shtml)

+1

---

### Post by mr32 on 2010-11-11
Perfect solution, but the 1920x1080 resolution doesn't work :(.
Maybe I can try it in a smaller 16:9 resolution (1366x768), but is there a command to see which resolution plymouth support?

---

