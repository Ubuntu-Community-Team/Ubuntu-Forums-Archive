---
title: "How to change TTY resolution?"
date: 2009-06-12
forum: General Help
---

### Post by Mike.lifeguard on 2009-06-12
I'd like to change the TTYs on CTRL-ALT-F[1-6] so they have a higher resolution. The instructions at [https://help.ubuntu.com/community/ChangeTTYResolution](https://help.ubuntu.com/community/ChangeTTYResolution) don't show anything for my screen resolution:
```

mikelifeguard@mikelifeguard-laptop:~$ xdpyinfo | grep dimensions
  dimensions:    1280x800 pixels (330x210 millimeters)

```

I guess that will also change the resolution for the boot messages, which will be nice too.

---

### Post by unutbu on 2009-06-12
Have you tried vga=795 or vga=792?

Also would setting the font to something smaller be of interest to you?

---

### Post by tomd123 on 2009-06-12
1280x800 sounds like a laptop resolution. If you have intel graphics, try "vga=864". That's the 1280x800 vga code for intel graphics. It's not standard so you probably will have a hard time finding it anywhere else :D

---

### Post by Mike.lifeguard on 2009-06-14
> **tomd123 said:**
> 1280x800 sounds like a laptop resolution. If you have intel graphics, try "vga=864". That's the 1280x800 vga code for intel graphics. It's not standard so you probably will have a hard time finding it anywhere else :D

Yes, it's a laptop & yes it is intel graphics. I'll give 864 a try on my next boot...

Thanks!

---

### Post by MaxIBoy on 2009-06-14
vga=864 worked like a charm for me on my Toshiba Satellite. 

Don't need it anymore, though-- I compiled my own kernel, and now I use kernel mode-setting! It auto-magically detects the highest resolution. Also, switching between the virtual terminals (that's what they're called) is instantaneous.

---

### Post by Mike.lifeguard on 2009-06-15
> **MaxIBoy said:**
> vga=864 worked like a charm for me on my Toshiba Satellite.

For me, vga=864 makes the terminals into blank black screens, and the boot messages disappear (despite the 'quiet' option being removed).

---

