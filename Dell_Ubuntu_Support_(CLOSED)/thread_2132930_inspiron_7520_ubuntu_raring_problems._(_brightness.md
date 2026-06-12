---
title: "inspiron 7520 ubuntu raring problems. ( brightness, hd 4000 tearing, amd 7730m )"
date: 2013-04-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by xfcewithmutter on 2013-04-06
1) intel hd 3000/4000 series always do tearing in  opengl/composite output when rc6 mode enabled. affected mutter (clutter option fix not real solution), compiz ( version 9.8 opengl es sync system not real solution ), all kde kwin variants. this is oldy bug no one can nothing. this bug  broken compiz mutter kwin performance. im broken one laptop when trying modded bioses. sample:[http://www.youtube.com/watch?v=jK3L-n5_OX0](http://www.youtube.com/watch?v=jK3L-n5_OX0)

2) i can disable radeon 7730m from vga switcheeroo but i cant use 7730m gpu. when i used "echo ddis > ........."  option and triggered "next X session will use radeon gpu" option its not work. im logout and system not response. black screen.

3) when i installed lastest fglrx beta driver from amd vsync cant work. and system only run in 7730m gpu display.  when i select intel gpu from amd control center. its not work system locking at new restart. when i remove xorg.conf X can start again with default xorg-server-intel output. 

why i can do this:    close amd gpu and start default internal gpu.    or start with amd gpu.

4) when i used ubuntu raring ( or kernel 3.8 with ubuntu 12.10 or 12.04 )   i must use "acpi_backlight=vendor" option.    this problem not on kernel 3.2,   3.4 or 3.5 ( ubuntu 12.04 or 12.10 ). and brightness slider moving harder. its using %100 cpu when used slider. something wrong with this.

---

