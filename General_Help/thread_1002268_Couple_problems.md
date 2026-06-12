---
title: "Couple problems"
date: 2008-12-04
forum: General Help
---

### Post by munit5000 on 2008-12-04
I have recently installed ubuntu intrepid ibex 8.10 (< 2 days) and everything worked well except for a few things:

1) I don't have a boot screen anymore, I don't recall when this started happening. The ubuntu loading bar doesn't show up on boot, and boot times take 30-40 seconds on a fast laptop that is new. (high priority)

2) No backlight support on my Sony Vaio VGN-FW290, which eats up a lot of battery life. On vista I can easily get 4 hours battery life with a low backlight, but I can't change it on ubuntu. (high priority)

3) How do I import songs off a device using rythmbox? I got it to recognize my iriver clix, but it can only play songs off of it, and not rip the music on it to my hdd. (low priority)

If anyone knows any solutions to these problems I'd be really grateful if you could help me out.

---

### Post by munit5000 on 2008-12-04
Does anyone know how to install

[http://www.linux.it/~malattia/wiki/index.php/Sony-laptop](http://www.linux.it/~malattia/wiki/index.php/Sony-laptop)

This might fix my backlight problem. I looked on the package manager and I couldn't find it. How do I check if I have this file?

---

### Post by CaseWestern on 2008-12-04
> **munit5000 said:**
> I have recently installed ubuntu intrepid ibex 8.10 (< 2 days) and everything worked well except for a few things:

1) I don't have a boot screen anymore, I don't recall when this started happening. The ubuntu loading bar doesn't show up on boot, and boot times take 30-40 seconds on a fast laptop that is new. (high priority)

2) No backlight support on my Sony Vaio VGN-FW290, which eats up a lot of battery life. On vista I can easily get 4 hours battery life with a low backlight, but I can't change it on ubuntu. (high priority)

3) How do I import songs off a device using rythmbox? I got it to recognize my iriver clix, but it can only play songs off of it, and not rip the music on it to my hdd. (low priority)

If anyone knows any solutions to these problems I'd be really grateful if you could help me out.

for your first question follow this thread [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

And for the second one may be you should stop using the 3-d effects if you are using any.....

---

### Post by falcon61102 on 2008-12-04
I don't have a Sony Vaio so I'm not positive on this one, but I did some searching around and you might want to take a look at this HOWTO:

[http://ubuntuforums.org/showthread.php?t=88611&highlight=sony+backlight](http://ubuntuforums.org/showthread.php?t=88611&highlight=sony+backlight)

That addresses the issue with your backlight and it seems to go over some of the issues that were posted on the wiki link that you provided.

---

### Post by munit5000 on 2008-12-05
So I reinstalled 8.10 over my old ubuntu that I managed to mess up somehow. This one has it's boot screen and by that I mean the loading bar that ubuntu shows up, not GRUB. As for the Sony Vaio post, I already had seen that and the problem with it is that spicctrl is not in the repository anymore. Seems [http://www.linux.it/~malattia/wiki/i...hp/Sony-laptop](http://www.linux.it/~malattia/wiki/i...hp/Sony-laptop) is still the closest thing I've got to a fix.

---

### Post by falcon61102 on 2008-12-05
Your GRUB may just be hidden.  If you need to get to the GRUB, press ESC right after the BIOS gets done loading and you should be good to go.  You'll see some text in the upper right about loading and pressing ESC, that would be the time to do so.

That's unfortunate about that thread, I realize it was ancient but there were some recent posts in there so I was hopeful.  Hopefully this will be address for you in future updates.

---

