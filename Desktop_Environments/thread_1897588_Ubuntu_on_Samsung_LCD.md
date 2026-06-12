---
title: "Ubuntu on Samsung LCD"
date: 2011-12-19
forum: Desktop Environments
---

### Post by snailrider on 2011-12-19
Hi All,
I just plugged in my PC to my 40" Samsung LCD TV but the system shows the display is unknown. Hence doesnt let me to change the resolution anything higher than 1o24x 768. My LCD could do lot better than that, so I wonder what do I have to do to have Ubuntu realise the make and model of my TV. Again, this is not a desktop monitor, it's a proper TV which has an PC analog VGA input so I just thought it would work

I also assume I should install the graphics driver. Since I dont know that how to do, I have a Gigabyte GA-G31M-S2L motherboard and using it's integrated graphics solution.

Thanks

---

### Post by snailrider on 2011-12-24
I thought I write it down here, because I found a solution. The credit is not mine, somebody posted this a while ago on ubuntugeekz..
 
1st step:
cvt 1920 1200
 
2nd step:
take the output of the first command and run
xrandr --newmode <output from first command> 
 
3rd step:
xrandr --addmode VGA1 1920x1200_60.00
 
4th step:
xrandr --output VGA1 --mode 1920x1200_60.00
 
to make this whole stuff permanent, add the same commands from step 2, to the /etc/gdm/Init/Default file, right after the section OLD_IFS=$IFS
 
that's it.

---

