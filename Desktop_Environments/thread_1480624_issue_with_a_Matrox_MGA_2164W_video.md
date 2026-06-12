---
title: "issue with a Matrox MGA 2164W video"
date: 2010-05-11
forum: Desktop Environments
---

### Post by quada93 on 2010-05-11
hi,

I've installed ubuntu 10.04 LTS. Everything works fine except for the video (a MGA 2164W [Millennium II]) display. I followed some instructions on the web and got the following info as far as my video.

sudo lshw -C video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82815 Chipset Graphics Controller (CGC)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f4000000-f7ffffff(prefetchable) memory:ff000000-ff07ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: MGA 2164W [Millennium II]
       vendor: Matrox Graphics, Inc.
       physical id: 8
       bus info: pci@0000:01:08.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vga_palette
       configuration: latency=64
       resources: memory:f8000000-f8ffffff(prefetchable) memory:fdffc000-fdffffff memory:fd000000-fd7fffff memory:80000000-8000ffff(prefetchable)
anhduy@Paris:~/Downloads$ 

Could someone show me how to properly configure the video. Thanks.

---

