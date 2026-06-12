---
title: "Ubuntu Feisty CK Kernel (i386)"
date: 2007-04-22
forum: Desktop Environments
---

### Post by Derevko on 2007-04-22
These are patches designed to **improve system responsiveness** with specific emphasis on the desktop, but suitable to any workload.

Installing this kernel you have:

[LIST=1]
[*]686 (Pentium4) or Core2 optimization
[*]Ck patch [http://members.optusnet.com.au/ckolivas/kernel/](http://members.optusnet.com.au/ckolivas/kernel/)
[/LIST]

Add the gpg key:

```
wget http://ubuntu.iuculano.it/AE3BE9AA.gpg -O- | sudo apt-key add -
```

Add the sources.list entries in a separate file:

```
echo "deb http://ubuntu.iuculano.it gutsy all" >/etc/apt/sources.list.d/ck-kernel.list  
```

```
sudo apt-get update
```

For 686 (Pentium4):

```
sudo apt-get update && sudo apt-get install linux-686-ck linux-headers-686-ck
```

For core2:

```
sudo apt-get update && sudo apt-get install linux-core2-ck linux-headers-core2-ck
```


Feedback are welcome :)

---

### Post by midtown on 2007-07-24
So, is the 686 applicable to laptop Pentium M chips?

And to make sure I understand correctly, this is applying the -ck patchsets to the kernel? I would have thought you would have to recompile for that to work.

Thanks for this, I look forward to perhaps following it after I understand a little better.

---

### Post by mandragore on 2007-08-22
OK, done it, now X.org is no longer working. Any ideas on how to reverse it? :-) Thanks.

---

### Post by Milk &amp; Toast &amp; Honey on 2007-08-23
[QUOTE="mandragore"]OK, done it, now X.org is no longer working. Any ideas on how to reverse it?  Thanks.[/QUOTE]
Hi, are u using nvidia proprietary driver?
If yes, i think you should re-install the driver.
Another way, you can choose to boot the old kernel from grub.
Here's how:
After booting your computer, when there's text written "GRUB xx Loading...", just repeatedly press "ESC" button, and select your previous kernel (something like 2.6.20-15-generic or 2.6.20-16-generic). 

BTW, you're a bit luckier than me, after installing those kernel, my machine won't even boot, no matter what kernel I choose to boot, I had to re-install my feisty, my-o-my, what a dangerous game for noob :) .

---

### Post by Derevko on 2007-11-11
Updated for gutsy

---

### Post by mukiex on 2007-12-21
Derevko, thank you SO much. The word really needs to get out about this patch. I now call it my "DDR" or "Half Life 2" or "frickin' performance usability" patch.

Let me explain. With this patch, I'm not sure if HL2 performs better or not (the framerate might be a little lower) but it's DEAD ON STABLE. It's stable the likes of which I haven't seen on WINDOWS. You know the dreaded Half-Life 2 stutter? It's GONE with this patch (I've dealt with it in both Win XP and Ubuntu under Wine). I made jokes about how I couldn't play Portal because I had it running in Wine under Compiz with Handbrake converting a DVD in the background, but with the patch, under those settings, I can play it just fine.

What more, it moved Stepmania from "Un-frickin'-playable, even with Handbrake reniced to 19, even after I quit out of Handbrake, even with Compiz turned off, on a CORE TWO BLOODY DUO" to "Plays just fine, not a single stutter or note missed (at least not missed because of a stutter)".

I'm gonna keep seeing how it affects things, but right now CK just made DRASTIC changes into how I think about my computer's performance. It's really quite unfortunate he stopped development. How does CFS compare to it?

P.S. The HL2 stutter problem hit me really hard in Portal, because it would come out almost every other time I generated a portal, and the stutter would get so bad I'd hit the wrong spot. I just beat the game again to test the patch, with a bunch of apps running, and I didn't get a SINGLE stutter throughout. It's insane.

---

### Post by mukiex on 2007-12-22
Test 2 : Seriously, this is the greatest patch ever for whatever Stepmania fans have tried getting it running in Ubuntu. I just reniced HandBrake to 19 while it was doing its work. Stepmania doesn't ever go above 10% (measuring with "top", if there's a more accurate way I'll try that) CPU, so Handbrake's performance is barely affected if at all, but the DDR sim itself runs silky smooth to a level I don't think I saw in Windows. Seriously, I can only hope CFL is as good as this patch, because its performance is beautiful.

---

### Post by midtown on 2007-12-22
Thanks for the update for Gutsy! Can anyone confirm or deny that the 686 is applicable for a Pentium M? I would GREATLY appreciate it.

---

### Post by Xelinis on 2008-01-09
I have a regular Core Duo: which should I apply?

---

