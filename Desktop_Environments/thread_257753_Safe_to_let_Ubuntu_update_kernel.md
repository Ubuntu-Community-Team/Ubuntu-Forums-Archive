---
title: "Safe to let Ubuntu update kernel?"
date: 2006-09-15
forum: Desktop Environments
---

### Post by n00buntu NJ on 2006-09-15
I'm seeing a bunch of people losing the desktop after the update...  I know that there is something about having to reinstall drivers after kernel updates, but I'm using the nvidia-glx driver which will also be updated during this auto update...

Is it safe to give it a shot?

---

### Post by aysiu on 2006-09-15
I just updated and everything was fine. I can't guarantee it'll be safe on your box, though.

---

### Post by karamba_kid on 2006-09-15
I thought the same thing and updated and lost my desktop.  I have all the latest updates but X is still refusing to start, it says there are problems with the nvidia-kernel-module.  I'm hoping for more updates soon.

---

### Post by n00buntu NJ on 2006-09-15
> **aysiu said:**
> I just updated and everything was fine. I can't guarantee it'll be safe on your box, though.

So you just let it rip - kernel and nvidia-glx all at once?  

Hmmm...  It's a little scary for me cuz I've got compiz running so beautifully right now...

---

### Post by aysiu on 2006-09-15
I don't have Compiz or XGL.

---

### Post by karamba_kid on 2006-09-15
I don't have compiz or xgl and the updates still broke my desktop.

---

### Post by majesticturkey on 2006-09-15
I have compiz/xgl, but don't use them currently. I run fglrx drivers for my ATI card. I let 'er rip and everything worked beautifully. Except for some reason GRUB calls it "Debian GNU/Linux." Typo on Ubuntu's part :P

---

### Post by musicinmybrain on 2006-09-15
> **karamba_kid said:**
> I thought the same thing and updated and lost my desktop.  I have all the latest updates but X is still refusing to start, it says there are problems with the nvidia-kernel-module.  I'm hoping for more updates soon.

If you have compiled the latest nvidia or ati proprietary drivers from the manufacturer, then you must recompile them after each kernel update. If you're using the nvidia-glx from the repositories, then of course you don't need to recompile anything. Apologies if this isn't relevant to your problem.

---

### Post by SvanteH on 2006-09-15
Worked fine for me.

---

### Post by someguyouknow on 2006-09-15
updated just now and had no problems...

---

### Post by peabody on 2006-09-15
There was a thread floating around here about how the kernel update breaks the nvidia drivers.  Anyone not using the Nvidia drivers is supposedly fine.  The very latest update, (one after 20:00 UTC on Sept14 I believe) supposedly fixes the problem.

---

### Post by akshaysrinivasan on 2006-09-15
I lost my destop in breezy once too.My suggestion go Synaptic and update only to the official verison of the kernel (with the logo on its left).

---

### Post by n00buntu NJ on 2006-09-15
> **musicinmybrain said:**
> If you have compiled the latest nvidia or ati proprietary drivers from the manufacturer, then you must recompile them after each kernel update. If you're using the nvidia-glx from the repositories, then of course you don't need to recompile anything. Apologies if this isn't relevant to your problem.

Now THAT's what I wanted to hear...  

Thanks!

---

### Post by karamba_kid on 2006-09-15
I am using the nvidia-glx package and I have all the latest updates (restricted-modules, kernel, etc.) however X is still broken and nvidia complains about an unknown symbol "boot_cpu_data".  I doubt that a fix is being worked on, so I will be switching distros this weekend, probably to Debian.  Ubuntu was nice when it worked, but I can't deal without having X server work.

---

### Post by Saibot on 2006-09-15
Update worked fine for me - using nvidia-glx drivers here.

---

