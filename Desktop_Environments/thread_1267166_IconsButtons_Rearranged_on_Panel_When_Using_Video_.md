---
title: "Icons/Buttons Rearranged on Panel When Using Video Projector"
date: 2009-09-15
forum: Desktop Environments
---

### Post by arnold.pietersen on 2009-09-15
Hi

Just checking.

When I use a video projector, the icons/buttons are rearranged on the panel. Most probably due to the fact that the screen change to 800x600 then I have to change it to 1024x768 when I connect a video projector.  Mind you, 1280x800 is not available when I use a video projector.

Any help will be appreciated.

---

### Post by steveneddy on 2009-09-15
What type or brand of video card are you using?

---

### Post by arnold.pietersen on 2009-09-15
Hi Steveneddy

The following are the details for my VGA card:

Model: 82852/855GM Integrated Graphics Device
Vendor: Intel Corporation (Toshiba America Info Systems)

I hope this helps

Thanks

---

### Post by theZoid on 2009-09-16
I use Nvidia and that doesn't happen to me.  I've heard of it happening with others just like you and heard it was a 'bug' that's been around for years.

---

### Post by steveneddy on 2009-09-17
Sorry it took so long to get back.

I travel for a living and sometimes it's hard to get back immediately.

Try this:

```
xrandr --output VGA --auto
```

Here's the link to a bugs page in Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel)

---

