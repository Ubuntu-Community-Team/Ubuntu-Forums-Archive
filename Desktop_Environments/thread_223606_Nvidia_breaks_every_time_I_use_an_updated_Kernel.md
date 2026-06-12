---
title: "Nvidia breaks every time I use an updated Kernel"
date: 2006-07-26
forum: Desktop Environments
---

### Post by maruchan on 2006-07-26
Can anyone tell me why this happens and how I might fix it? Loading the Nvidia kernel module fails every time I try to start up with a new kernel that the update-manager has given me. I can use VESA just fine but the 60Hz refresh rate kills my eyes.

My current kernel, 2.6.15-23-k7, works fine with Nvidia but I believe I somehow configured it months ago and it "accidentally" worked.

I searched the forum for solutions so I could get the newer kernel updates working with Nvidia, but there were so many different ideas given that I was confused (don't want to break anything...)

Any help is appreciated :)

---

### Post by FenrisAbraxas on 2006-07-26
> **maruchan said:**
> Can anyone tell me why this happens and how I might fix it? Loading the Nvidia kernel module fails every time I try to start up with a new kernel that the update-manager has given me. I can use VESA just fine but the 60Hz refresh rate kills my eyes.

My current kernel, 2.6.15-23-k7, works fine with Nvidia but I believe I somehow configured it months ago and it "accidentally" worked.

I searched the forum for solutions so I could get the newer kernel updates working with Nvidia, but there were so many different ideas given that I was confused (don't want to break anything...)

Any help is appreciated :)

Every time you change your kernel you have to recompile nvidia drivers :P

---

### Post by maruchan on 2006-07-26
Whoa, are you serious? I had no idea. Can you give me any links for that, or tell me how to do it? Thanks.

---

### Post by _simon_ on 2006-07-26
I always find that method 1 here works just fine:

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by bensexson on 2006-07-26
If you use the nvidia-glx drivers in the repositories they will be updated with the kernel.

---

### Post by maruchan on 2006-07-26
Thanks to everyone for the replies. I noticed that my new kernels were 686 kernels, while the one that worked with the nvidia driver was a K7 kernel. Figuring this might have something to do with the problem, I did this:

```
sudo apt-get install linux-k7
```

Somehow I had installed a K7 kernel without installing this package. After getting the newest K7 via that command, I rebooted into the shiny new K7 kernel and everything worked!

Thanks again!

---

### Post by maruchan on 2006-07-26
BTW I should ask - is there some package I need to remove so I stop getting 686 and 386 updates to the kernel, or is that not a good idea?

---

### Post by orb9220 on 2006-07-26
I think you have to actually remove them. Which I read is fine if you are not 
booting them.

---

