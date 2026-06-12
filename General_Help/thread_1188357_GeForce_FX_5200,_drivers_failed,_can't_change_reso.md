---
title: "GeForce FX 5200, drivers failed, can't change resolution"
date: 2009-06-15
forum: General Help
---

### Post by madnessjack on 2009-06-15
Hi guys,

I'm new, and I've had jaunty studio for about a week now. I've got two problems regarding my nVidia GeForce FX 5200 graphics card. Basically, it wont have the drivers (any!) and I can't change resolution.

I've got an old LCD TV and in windows it's a breeze to open up the nvidia cp and force the resolution up, but EDID info says it maxes out at 800x600. In xp I've got it at 1600x1024 and it looks alrite.

I've tried all the nvidia drivers and even got envyNG to automate it just incase I was being silly. After envyNG does it's thing or I run nvidia-xconfig, the nvidia reports as failed on bootup and it defaults to a console so I have to dpkg-reconfigure my way out.

This little card is fine for all my windows needs and I'd hate to have to get a new one because janty wont have it. I'm not too bothered about 3D or acceleration (although obviously that'd be a plus), but is there anyway I can change resolution? I've tried xconfig and xrandr and failed.

Here's what my xrandr says:
```
jack@garage-pc:~$ xrandr --newmode "1600x1024" 137.16 1600 1672 1840 2152 1024 1024 1026 1062
jack@garage-pc:~$ xrandr --addmode default "1600x1024"
jack@garage-pc:~$ xrandr -s 1600x1024
Failed to change the screen configuration!

```

And it says a similar thing for the display cp.

Please, anyone, help me!

Many thanks,
Jack

---

### Post by madnessjack on 2009-06-16
So I've given up with the resolution problem and connected a modern monitor to my machine and it works fine. But the nvidia drivers still won't work. The recommended version for my card is 173.14.xx and I've even tried compiling them myself from the nvidia website but the installer fails with "could not create kernel" (or similar message).

If anyone could help out here I'd be very grateful. Any suggestions of things I haven't tried yet etc.

Many thanks

---

### Post by nolliecrooked on 2009-06-16
> **madnessjack said:**
> So I've given up with the resolution problem and connected a modern monitor to my machine and it works fine. But the nvidia drivers still won't work. The recommended version for my card is 173.14.xx and I've even tried compiling them myself from the nvidia website but the installer fails with "could not create kernel" (or similar message).

If anyone could help out here I'd be very grateful. Any suggestions of things I haven't tried yet etc.

Many thanks

lol leicester...

anywayyyyy... how did you try to install them in the first place?

---

### Post by madnessjack on 2009-06-16
"sudo apt-get install nvidia-glx-173"

I've even tried Add/Remove Programs, the Syaptic Package Manager, Hardware Drivers and EnvyNG. I used "sudo apt-get remove nvidia*" to remove them each time.

> **nolliecrooked said:**
> lol leicester...
What's so funny about Lesta? lol


I've also followed the instructions on this post
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

And tried the patch here
[http://www.nvnews.net/vbulletin/showthread.php?t=134461](http://www.nvnews.net/vbulletin/showthread.php?t=134461)

But no luck :P

---

### Post by nolliecrooked on 2009-06-16
try;

sudo aptitude remove nvidia-glx-173

and see what happens.

---

### Post by madnessjack on 2009-06-16
And I bet you love walkers crisps :P

Anywho, cheers for the info, I'll give it a go when I finish work and let you know how it goes

Thanks!

---

### Post by nolliecrooked on 2009-06-16
> **madnessjack said:**
> And I bet you love walkers crisps :P

Anywho, cheers for the info, I'll give it a go when I finish work and let you know how it goes

Thanks!

later bro o/

---

### Post by madnessjack on 2009-06-16
Hey,

Well I removed a good chunk of crap from nvidia, but I'm still not having any joy trying to compile the ones from the nvidia website.

[http://www.nvidia.co.uk/object/linux_display_ia32_173.14.18_uk.html](http://www.nvidia.co.uk/object/linux_display_ia32_173.14.18_uk.html)

I just get a "could not create kernel" error message and it goes no further. I've even ran it in recovery mode. With this different monitor I can get a decent resolution, but no hardware acceleration.

Cheers anyway mate :)

---

