---
title: "Flash causing tearing in browser"
date: 2011-03-20
forum: Desktop Environments
---

### Post by Enigmatic on 2011-03-20
I've noticed lately that when scrolling, the video "tears" and moves along with my scrolling on sites such as Youtube, when it should be fixed in position. Note that it doesn't actually move perfectly and is flickery/cropped while scrolling. I have all the latest updates (10.10) and notice it in both Chromium and Firefox, so it's either the window manager or ATI driver. Any ideas?

---

### Post by gordintoronto on 2011-03-20
How fast is your computer? How much memory, what video card?

If you are watching a video on Youtube, and you scroll the web page, the video should move.

---

### Post by Enigmatic on 2011-03-20
It may be limited just to Youtube, I'm not sure. I have also noticed that pdfs do not display using the Adobe reader plugin after sometime and I have to restart Firefox. It seems like another windowing related issue.

This is what I see when scrolling on Youtube. It takes a little bit to correct itself. My PC is not the problem, it's an E8400 (3GHz), 8GB RAM, SSD, x64 Ubuntu.

---

### Post by gordintoronto on 2011-03-20
You're right, your computer should not be the problem.

I would suspect the video driver, but not with any confidence.

---

### Post by RobbieThe1st on 2011-03-21
More than likely it's the flash plugin - IIRC, recent versions have HW acceleration support(At least the x64 "beta" version does on my Nvidia-based system), and that seems to have some odd effects, due to it using color-based transparency(That is, some color is chosen that is "transparent" - when the video card composites the video frames with everything else, it pastes it over pixels of that color) - If I had another window with the transparency color showing, the video would show through for those pixels of that color. Quite a problem if the transparency color is black or white ;)

I ended up fixing my problems through an xorg.conf option named "TransparentIndex", but as that's a nvidia-option, you should look in your video driver manual for an option like that you can try.

---

### Post by ibrahim.shakra on 2011-03-21
I am using ubuntu since a while & firefox is slow on ubuntu & I installed chrome it's working better with flash now & better than fire fox  too.

---

### Post by Enigmatic on 2011-03-22
I am no longer seeing this issue on the PPA version of Firefox 4. Sunspider benchmarks are also faster than Chromium's. :)

---

