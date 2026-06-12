---
title: "Ubuntu recognize my screen as CRT - Resolution Problem"
date: 2011-06-24
forum: Desktop Environments
---

### Post by larxi on 2011-06-24
Hello ubuntu-users!

I have installed ubuntu 11.04 and everything runs smoothly except the resolution I get. 
I use the VGA input of my screen because DVI is dead and everything seems huge in my screen! 
Even if I change the resolution the display exceeds the boundaries of my screen!

Any ideas how to fix this?

Thank you very much!!

---

### Post by larxi on 2011-06-24
No one? Any ideas?

---

### Post by FormatSeize on 2011-06-24
> **larxi said:**
> 
I use the VGA input of my screen because DVI is dead and everything seems huge in my screen! 
Even if I change the resolution the display exceeds the boundaries of my screen!
11.04, when it comes to anything nonstandard or oddball, doesn't do well with nonstandard video setups. In my case, I have an oddball monitor (1440X900), and the grub screen won't properly resolve. 
 
As for your case, using VGA as the output is likely not something that 11.04 expects to be happening when a standard video output is present. The other day, I changed my processor, and for whatever reason, the only output that would show up was the VGA. Normally, that results in a case that you experience with everything become huge. But, I went into my BIOS and set VGA as the primary output, and the display showed up normally. You should try that and see if it does anything for you.
 
The reason behind everything becoming large is because the VGA output you are using is most likely 640X480 pixels. Does VGA work with other Ubuntu releases for you?

---

### Post by larxi on 2011-06-25
Thank you for your reply FormatSeize!

I am not using an onboard display output but NVIDIA G210. I don't have any experience with other Ubuntu releases. 
Now that I use an adapter with DVI output I get an option of 1360x768 but when I select it everything goes out of the screen's boundaries. 

Any ideas how to fix it? I am not using screen's DVI because it's dead.

Thank you for your time!

---

### Post by mcduck on 2011-06-26
If the resolution is right for your display, then it's just a matter of using the *display's* controls to adjust the image to correct size & position.

Also, based on the resolution, is it perhaps a HD-Ready television? In that case make sure you have set it to unscaled, pixel-per-pixel mode, whatever that's called on your television. Otherwise overscan will result in some of the image going beyond the displays visible area (and the visible image being more or less blurry as a result from the display scaling the image).

Of course you should have the correct drivers for your graphics card as well. If the resolution you are now getting isn't the right one, graphics drivers are what in most cases fixes the issue.

---

