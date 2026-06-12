---
title: "Alternative to Xubuntu?"
date: 2009-04-23
forum: General Help
---

### Post by chessnerd on 2009-04-23
I'm currently running Xubuntu 8.10 (hopefully 9.04 soon :)) and I like it a lot. The piece of hardware I'm using runs it pretty well (1.7Ghz P4, 256MB RAM), but I recently got another (even older) computer that I wanted to install Linux on. My first choice was Xubuntu, but, upon learning that the computer only has 128MB of RAM and a 1.1Ghz Athlon processor, I skipped that idea. (I know that Xubuntu can work with 128 RAM, but right now, with just Opera running, I'm at 167MB)

I've read about really small Linux distros like DSL and Puppy, but, when I tried out the Live CDs, I didn't care much for the JWM desktop.

I was wondering if anyone knew of a distro using Xfce that was smaller than Xubuntu? If there isn't one, what should I do with the computer?

---

### Post by elamericano on 2009-04-23
I think Zenwalk is a little smaller. I've been meaning to try it.

---

### Post by por100pre1 on 2009-04-23
I would have answered "Puppy Linux" but you have already considered that. The problem here is that in order to achieve the best performance in Xfce you should try to use only GTK+ applications. Opera uses Qt libraries which are also loaded in order for Opera to run.

---

### Post by kanikilu on 2009-04-23
The only others I've tried recently are LXDE and Fluxbox. If it will run LXDE, that might be the closest you can get to a desktop environment like XFCE. Fluxbox is even more lightweight, but extremely minimal...

Did you already check out this page? [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by adamlau on 2009-04-23
Out of the box? VectorLinux. Though I would also suggest both Ubuntu Minimal + Xfce and Arch + Xfce. Consider going BSD with NetBSD + Xfce. And JWM really is nifty and fast once properly configured (I cannot feel  a difference in response versus dwm). 1.1Ghz 128MB? That system is going to struggle with any DE/WM, even my 1.7GHz 256MB with NetBSD (everything installed through pkgsrc) + JWM (as minimal a build as JWM can be built) lags.

---

### Post by chessnerd on 2009-04-23
I'll take a look at Zenwalk and Vector and see how well they work.

> **kanikilu said:**
> If it will run LXDE, that might be the closest you can get to a desktop environment like XFCE.
I'd be interested in trying that desktop environment out. Do you know any good distros that either come with LXDE or that I can add it to?

---

### Post by kerry_s on 2009-04-23
> **chessnerd said:**
> I'm currently running Xubuntu 8.10 (hopefully 9.04 soon :)) and I like it a lot. The piece of hardware I'm using runs it pretty well (1.7Ghz P4, 256MB RAM), but I recently got another (even older) computer that I wanted to install Linux on. My first choice was Xubuntu, but, upon learning that the computer only has 128MB of RAM and a 1.1Ghz Athlon processor, I skipped that idea. (I know that Xubuntu can work with 128 RAM, but right now, with just Opera running, I'm at 167MB)

I've read about really small Linux distros like DSL and Puppy, but, when I tried out the Live CDs, I didn't care much for the JWM desktop.

I was wondering if anyone knew of a distro using Xfce that was smaller than Xubuntu? If there isn't one, what should I do with the computer?

i use old stuff, the thing i learned is size does not matter, it's whats running that counts. you should try doing a custom install, building up from a base install, gives the best results. any base install distro will do, i currently use arch. i have a 450mhz 256mb ram and a 700mhz 128mb ram both running arch.
jwm is fantastic for those that learn to use it, but you can try fluxbox or openbox, maybe even lxde.

i use jwm, it gives me a lot of options for setup and it's very low resource.

---

### Post by snowpine on 2009-04-23
Similar to Xubuntu (which rules out DSL, Puppy, etc in my opinion) but better for older hardware?

AntiX is my suggestion; it is based on Debian (which will be familiar to any Ubuntu user) but is specifically designed to run in 128mb of ram as a design goal. It uses your pick of the Icewm or Fluxbox desktop.

My favorite Xfce distro is Sidux, also based on Debian. I am a big Openbox/LXDE fan too: SliTaz, CrunchBang, and Debian Lenny LXDE for example. (Note: The distros in this paragraph are all 256mb-friendly, but borderline for 128mb.)

---

### Post by chessnerd on 2009-04-24
Okay, I downloaded a Vector Live disk to try out the OS and it didn't work. I put in the disk drawer on my laptop, which I've used to load up several Live CDs before (Ku, Xu, and Ubuntu, along with DSL and Puppy), but it just spun and spun the disk before it ended up booting into Vista. 

I also downloaded a Vector Standard edition and tried to install it without trying it (because, at the moment, the computer is running a VERY crippled version of Windows ME so I don't care if it gets installed over) and, while it loaded the options screen, it couldn't load the kernel to install.

Any ideas what the problems might be?


I'm gonna try the Zenwalk Live CD tonight and I am going to do some more reading into Sidux, Arch, AntiX, and Debian Lenny. I still have my fingers crossed for getting XFCE to work, but I want to give LXDE a try, and IceWM looks promising too.

Also, I'd like to thank everyone whose given me suggestions. This is way more feedback than I was expecting and I'm glad to see that the Ubuntu Forums community is open to helping Linux noobs like me. :)

---

