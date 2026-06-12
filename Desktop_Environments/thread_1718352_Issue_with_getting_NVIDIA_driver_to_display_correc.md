---
title: "Issue with getting NVIDIA driver to display correctly"
date: 2011-03-31
forum: Desktop Environments
---

### Post by ultrakomm on 2011-03-31
Hello!

I have a problem with getting the picture to display properly on my HDTV. Using the regular driver (whichever that is) the picture displays flawlessly, but when I'm using the NVIDIA driver it displays really weird. 

This is what it looks like: [http://img194.imageshack.us/img194/7332/bild1wl.jpg](http://img194.imageshack.us/img194/7332/bild1wl.jpg)

As you can see the top and the right of the picture is missing, and there is a large black bar to the left of it.

Since it only does this with the NVIDIA driver I guess the driver is at fault here. The graphics card is a 8400GS and I'm running Xubuntu 10.10. The HDTV has a native resolution of 1366x768, and I've connected to it using HDMI.

I have tried messing around with overscan compensation in nvidia-settings, but it didn't help much.

What can I do to fix this? I find it incredibly frustrating. 

Help is much appreciated, thanks in advance!

---

### Post by Krytarik on 2011-03-31
I believe it's more a matter of input settings at the HDTV than a faulty video driver. So check the input options. I had a similar issue with the HDTV of my mom a while ago, when I set it up.

Greetings.

---

### Post by ultrakomm on 2011-04-01
There are no input options on the TV unfortunately. And I do indeed believe the NVIDIA driver is at fault, as I said, because the screen displays perfectly fine when I use the non-NVIDIA driver.

Anyone else?

Thanks in advance.

---

### Post by Krytarik on 2011-04-01
> **ultrakomm said:**
> And I do indeed believe the NVIDIA driver is at fault, as I said, because the screen displays perfectly fine when I use the non-NVIDIA driver.

You know that different video modes may result in different display geometrics, right!?
Are they exactly the same with both drivers, regarding resolution *and* refresh rate?

---

### Post by ultrakomm on 2011-04-01
Indeed they are, and indeed I do know that. Thanks for the help. Really.

---

### Post by jawilljr on 2011-04-01
What brand is the TV? The reason I'm asking is that most TV's nowadays have what is called a "Service Menu", and sometimes there is a video offset that adjust the picture left/right and up/down.

You could go [here.]("http://www.riddledtv.com/forums/tv-service-menu-codes-f13.html") to find the code.

Hopefully that fixes the problem.

Jerry

---

