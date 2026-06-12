---
title: "If you could start fresh..."
date: 2009-01-01
forum: General Help
---

### Post by mperedithe on 2009-01-01
Hey Everyone,

In another week or two a local computer tech shop, here is town, is building me a new custom system.  There are only two requirements that I have, 1) The OS must be Ubuntu 8.10, and 2) I need to be able to utilize two monitors.

I'd love to hear from the community some of their successes or horrors regarding hardware and Ubuntu.

So if you know of, or have heard of, a video card/motherboard/processor/etc that works great (or not) with Ubuntu share your stories.

Thanks Everyone!

---

### Post by kokkus on 2009-01-01
Maybe you can get some ideas here

[https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)

or

[http://hwdb.ubuntu.com/](http://hwdb.ubuntu.com/)

or

[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

Good luck with your new PC :)

---

### Post by Maheriano on 2009-01-01
I use nVidia graphics over ATI simply because the ATI driver seemed to be buggy or the video card I had simply wasn't compatible for some reason. Plus there's an nVidia control application in the package manager. Maybe I don't understand it well enough but I won't buy ATI for another of my Ubuntu boxes.

---

### Post by mikeyd612 on 2009-01-01
I agree with Maheriano, don't go with ATI. I went with ATI for my box when I was ignorant and was using windows, and the drivers can be an ugly situation with linux. The only other thing that I've run into is that I've had issues with the dual monitor setup. I have an old laptop that I use for media type stuff. I've got it hooked up to a tv so that I can watch my ripped movies on the couch. But trying it with linux gave me problems. Apparently there is a way to use drivers designed for windows in linux but it's a little too much work for just a media computer. I just put tiny xp on it. Most other hardware seems to be pretty well supported though. Good luck.

---

### Post by mperedithe on 2009-02-07
Hey everyone,
Thanks for the great feedback.  I took your advise and installed a video card with a nvidia chipset.  the computer works great! The dual monitor setup was a bit tricky mikeyd612 but here is how I got around it...

*I didn't want the twinview setting or xinerama.  I wanted each monitor to be a separate desktop.  To accomplish this I used EnvyNG software to help me with the correct driver and then I used the nvidia software to configure separate X screens.  The biggest problem was that the etc file could not be parsed after I set it up.  From the error screen there is a button offering to show you the file itself.  I opened the file and then copy pasted it into the editor.  From there I tweaked it with custom names for the two screens.  Then I opened the x config file (sorry, but I don't remember the exact name) deleted what was in it and pasted the new file.  Bingo! everything worked on reboot.*

Now, here is my own personal horror story from an installation a long time ago.  I tried to install Ubuntu on my wifes Dell Dimension and it would load but crash once it got to the desktop.  This was preventing me from installing it.  I tried Mepis, Suse, Dream, Mandrake, and a host of others and all failed.  After many trials I found that Fedora could be loaded fromt the live cd and then installed.  Now Fedoa is a nice distro but it was not the one that I wanted so two days of struggling and searching later I found the culprit.  A lot of the older Dell Dimensions used the Intel 3d chipset for the video.  For whatever reason linux had not developed a driver for this, hence the crashing.  So I went out and bought a cheap pci video card, slapped it in and eureka, I was able to load and install Ubuntu.

---

### Post by Maheriano on 2009-02-07
You should be able to configure the 2 separate monitors right in the nVidia control panel. You don't have to install anything else.

---

