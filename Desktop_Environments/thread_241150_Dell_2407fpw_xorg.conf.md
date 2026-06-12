---
title: "Dell 2407fpw xorg.conf?"
date: 2006-08-21
forum: Desktop Environments
---

### Post by qsub on 2006-08-21
I'm having a really hard time getting my monitor setup to display the correct resolution in Ubuntu.

I've tried to manually add a modeline but wasn't that successful, I googled the internet and only found modelines for the older model (2405FPW) which has different specs, I tried it anyways and it didn't work.

Does anyone here have a 2407fpw working correctly? If so, could you please post the xorg.conf for me?

Thank you!

---

### Post by mgpower0 on 2006-08-21
have you set up the correct drivers for any graphics cards/ integrated graphics chips etc. This is more than likley your problem if you have not. heaps of posts on these forums to do this just search for the one that suits you card/or chip

---

### Post by qsub on 2006-08-21
> **mgpower0 said:**
> have you set up the correct drivers for any graphics cards/ integrated graphics chips etc. This is more than likley your problem if you have not. heaps of posts on these forums to do this just search for the one that suits you card/or chip

I installed nvidia drivers through apt-get. I had a pretty crappy resolution like 1280x1050 stretched. After the drivers installed and I restarted, It didn't work.

I did try searching the forums here before I signed up to make this post.

---

### Post by Rastaman77 on 2006-12-29
Hi !

I also have a problem with X600 fgrlx, dual screen, 2 Dell 1280x1050 resolution monitor.

All work good in 1280x1050 cloned mode or single display (blender, fgl_gears), but when using dual head (by aticonfig --dtop=horizontal and adding Modes "1280x1024" in the server layout), fgl_gears display black window, and blender only show a part of it's interface.

Lower resolution is OK but display is awfull.

Is ATI supporting 1280x1050 resolution in dual head configuration ?

Anyone get that working ?

Thanks ! ](*,)

---

