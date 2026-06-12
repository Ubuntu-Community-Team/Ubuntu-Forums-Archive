---
title: "New Install of 9.04 Crashing"
date: 2009-06-08
forum: General Help
---

### Post by seagullplayer77 on 2009-06-08
OK...First things first, here's what I'm working with:

HP Pavilion dv9000 Series (2x AMD64, nVidia graphics, Atheros WiFi, 3GB RAM)

After reading so many good things about 9.04, I decided it was finally time to upgrade. My 8.04 worked great, but it was slow and I had installed a bunch of unnecessary junk over the past year, so I figured I would just start from scratch. I backed up all my pictures and documents and started installing Ubuntu Studio 9.04 64-bit from the DVD. Reformatted my former Linux partition with ext4 and began the install and for the most part, things seemed to be normal. After logging in, the problems started. My whole system started crashing, and most of the time Ctrl+Alt+PrtScr+REISUB didn't work either. My only option was a hard reset and after a few of those, the kernel started loading VERY slowly.

I figured the install must've been shoddy, so I started from scratch (again) and reinstalled 9.04. I found someone having similar problems who had fixed his crashing issues by adding the following options to the /boot/grub/menu.lst file:

```
nosmp acpi=off pnpbios=off
```

That seemed to work for a while, but once I started installing packages with Synaptic, my system crashed...again. Had to do another hard reset, and now I'm back where I started. It seems to be that the 64-bit realtime kernel is the main issue here and that the generic kernel works just fine, but the whole reason I use Ubuntu Studio is because I like having the realtime functionality for audio work.

I've also noticed that the boot options have negatively affected my dual core processing power. The second core is constantly running at 100%, according to htop, and the first core is hardly running at all.

Anyone have any ideas here? I thought 9.04 would be a good upgrade, especially since the new realtime kernel had undergone such extensive testing. Was I wrong?

Help me out here, guys.

---

