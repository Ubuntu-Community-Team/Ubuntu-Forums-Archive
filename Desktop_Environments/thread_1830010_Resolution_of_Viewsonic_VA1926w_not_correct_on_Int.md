---
title: "Resolution of Viewsonic VA1926w not correct on Intel D510MO motherboard"
date: 2011-08-21
forum: Desktop Environments
---

### Post by kyutums on 2011-08-21
I am using Ubuntu 11.04 on an Intel D510MO motherboard as a low-end surfing computer. The monitor, a Viewsonic VA1926w, has a maximum resolution of 1440x900. However, the monitor preferences shows a maximum of 1024x768 only. How can I bring up the resolution to 1440x900? The screen seems sort of flattened because of the incorrect settings.

I think the video card (built in) of the motherboard is an Intel  3150.

---

### Post by kyutums on 2011-08-21
I tried creating an xorg file via X -configure, but I got another error. :(
> (EE) Failed to load module "vmwgfx" (module does not exist, 0)
(EE) vmware: Please ignore the above warnings about not being able to to load module/driver vmwgfx
(++) Using config file: "/home/kyutums/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Number of created screens does not match number of detected devices.
  Configuration failed.
 ddxSigGiveUp: Closing log

---

### Post by characato on 2011-08-26
Hello, I found the solution here: [http://askubuntu.com/questions/41227/wrong-screen-resolution-on-an-intel-d510mo](http://askubuntu.com/questions/41227/wrong-screen-resolution-on-an-intel-d510mo)

I had to install a double screen tool found on Ubuntu Software center where I could see "both monitors" and I could turn the "laptop monitor" off and change the VGA to the resolution I wanted (1650x1080 in my case). I kept "both monitors on the same screen layout ant clicked on apply. It worked fine at that point but the screen settings got reseted after restarting ubuntu 11.04. So I did the same thing with the dual screen tool and then I went to the monitor tool that comes with Ubuntu and I could now see there was 2 monitors detected there too (before installing that dual monitor tool it only detected 1 monitor). I clicked ok and it saved the configuration. After that my settings stay fine after restarting Ubuntu.

I hope I'm clear. English is not my 1st language. If something is not clear, please let me know and I will explain differently.

Good luck!

---

### Post by kyutums on 2011-08-27
That worked. Thanks! :)

---

### Post by marcoharder on 2012-02-28
What utility should I look for in Ubuntu Software Center? I'm using the exact same motherboard.

---

