---
title: "How to uninstall Gnome &amp; GDM?"
date: 2006-09-09
forum: Desktop Environments
---

### Post by Lonthong on 2006-09-09
Hello,

I helped a neighbour installing edubuntu onto an old desktop for his kid.
The specs (pls don't laugh):
Pentium II 350mhz
Motherboard: Intel Se440Bx with Cirrus onboard sound
VGA: Asus V2740 (Intel 740 chipset) 8MB VRAM
Memory: 128MB
LAN: Realtek 8139
HD 3.1 GB

The installation itself was very smooth. Sound did not work out of the box but after reading through this forum, I managed to get it running.

However, the performance was rather sluggish and I intend to improve by installing WDM & fluxbox, replece firefox with Opera, etc..

As you may note, it only has 3 GB Hard disk so I think I must uninstall applications that are not neede.

My question is: Howto completely uninstall GDM & Gnome desktop environment w/o breaking anything??

---

### Post by rapha on 2006-09-09
Hi Longthong,

I don't think the installer does the same thing as aptitude and record what packages were only installed as a dependancy (please correct me if I'm wrong), so this might be rather tedious. However, gdm should be just 'gdm' and maybe 'gdm-themes'. I'd leave it installed tho (even got it working like a charm on my 300MHz iBook) and just remove whatever you can of GNOME (look for gnome in Synaptic and go through that list one by one) and replace it with XFCE. XFCE should be much more newbie-friendly than are the lot of *dm/Fluxbox/Blackbox/etc.

Regards,
Raphael

---

### Post by Lonthong on 2006-09-09
Reason for choosing WDM & Fluxbox was because I read somewhere that those are the lightest windows mgr available. If they are not newbie friendly, I may just forget the whole idea. Anyway, the kid is quite happy with it & did not make any complain.
Do you think XFCE will run sugnificantly better on above said system??
Is it also user friendly as Gnome??

---

### Post by meng on 2006-09-09
[http://psychocats.net/ubuntu/purexfce](http://psychocats.net/ubuntu/purexfce)
Look at the section "Removing Ubuntu". This is the command to remove all packages considered the ubuntu-desktop (i.e. GNOME).

---

