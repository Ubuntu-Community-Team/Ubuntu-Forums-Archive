---
title: "Configuring the ALPS touchpad? (Inspiron 1545 w/ Jaunty)"
date: 2009-05-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by madomac on 2009-05-06
Servus!

I installed the standard Jaunty amd64 release on my Dell Inspiron 1545. Works very well. Just the touchpad...

[LIST]
[*]No two/three finger tipping
[*]Random "false" clicks
[*]Inconsistent tap-and-hold dragging
[/LIST]
I think this could be fixed by configuring the synaptics driver that handles the ALPS touchpad. The touchpad seems to be capable of supporting multi-touch. I'd like to configure:

[LIST]
[*]Left mouse button via one-finger tap
[*]Right mouse button via two-finger tap
[*]Replace vertical scroll w/ scrolling via two-finger drag
[*]Nice and robust tap-and-hold dragging
[/LIST]
I tried my luck with changing the *.fdi-files in /usr/share/hal/fdi/policy/..., but without luck. Obviously my knowledge of Ubuntu is far from sufficient to do this right... ;)

Any expert here in the forum who has done this already? I'd like to use your *.fdi as a sample.

Thanks!
Marc

---

### Post by madomac on 2009-05-08
Anyone?! ;)

---

### Post by coffeeaddict22 on 2009-05-09
You _might_ be lucky; you might not.  Apparently the ALPS touchpad is the less configurable version of the Synaptics touchpad, and isn't quite so agreeable to being asked to do more than the basics.  Have a look at [this]("https://help.ubuntu.com/community/SynapticsTouchpad#hal") for some ideas.
Also, the xorg.conf that you'll have read about is pretty much deprecated for input devices.  If you read how to mess with it, don't bother; HAL or the Hardware Abstraction Layer has taken over most of it's job, although some display information still goes into it at present.  Have a look at [https://wiki.ubuntu.com/X/Config/Input]("https://wiki.ubuntu.com/X/Config/Input") for more info.

---

### Post by madomac on 2009-05-09
> **coffeeaddict22 said:**
> You _might_ be lucky; you might not.  Apparently the ALPS touchpad is the less configurable version of the Synaptics touchpad, and isn't quite so agreeable to being asked to do more than the basics.  Have a look at [this]("https://help.ubuntu.com/community/SynapticsTouchpad#hal") for some ideas.
Also, the xorg.conf that you'll have read about is pretty much deprecated for input devices.  If you read how to mess with it, don't bother; HAL or the Hardware Abstraction Layer has taken over most of it's job, although some display information still goes into it at present.  Have a look at [https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input) for more info.

Thanks for the info! I'll work through the links later. I already learned that the HAL and *.fdi-files are the way to go.

From what I read in the 'Net the ALPS touchpad built into the Inspiron 1545 should be highly configurable. And it supports various multi-touch gestures in Windows. So it should be able to teach that thinbg some decent behaviour... ;)

I'll come back with questions if necessary... :P

Cheers,
Marc

---

### Post by madomac on 2009-05-09
OK, I have a question... ;) What happens if I have multiple *.fdi-file referring to the same device via the "match" statement? Will they be carried out in a specific order, will they overwrite each other or will all the statements just be merged?

Thanks!
Marc

---

### Post by spidie on 2009-09-09
Any updates on what happened with this? Did you have any success? Would be great if you could share your findings. I have same problem with my Inspiron 1545 and these are a really common lowcost laptop at the moment.

I'm also having problems with random keystrokes - but that's for another forum post.

---

