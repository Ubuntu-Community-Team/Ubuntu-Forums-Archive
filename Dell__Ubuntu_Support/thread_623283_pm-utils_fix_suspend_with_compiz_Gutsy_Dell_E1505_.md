---
title: "pm-utils fix suspend with compiz Gutsy Dell E1505 / 6400 nvidia 7300"
date: 2007-11-25
forum: Dell  Ubuntu Support
---

### Post by Paul S on 2007-11-25
Ever since upgrading to 7.10 on my E1505 with nvidia 7300 card, I have had problems with suspend failing to resume.  It only happens when using compiz desktop effects.  It resumes successfully a few times, but then reboots or comes back with a black screen and non-functioning keyboard.

I recently saw a suggestion to try a package called pm-utils from Universe.  This seems to have fixed the resume failure problem with compiz.  Just to be safe, I uninstalled acpi-support, which took out powermanagement-interface and [x,k]ubuntu-desktop.  But, now I have functioning suspend and hibernate with compiz running!

Another problem is that the nvidia-glx-new driver has a bug that causes a freeze on 7x00 cards.  To fix this, I uninstalled the nvidia-glx-new and went back to the nvidia-glx.  However, there is now an nvidia 169.04 beta, which is running better on my 7300 card.  If you decide to use 169.04, you have to add into /etc/X11/xorg.conf into the "Screen" section:

```


Section "Screen"
Option  "UseCompositeWrapper"   "True"

< other stuff >

EndSection

``` I'd recommend this if you have the 7300 card on gutsy.

Dell Rocks! [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by Paul S on 2007-12-01
> **Paul S said:**
> now I have functioning suspend and hibernate with compiz running!


Apparently I spoke too soon.  After running with pm-utils for a week or so, now I find the same poor resume performance as occurs with acpi-support.

There is another alternative that seems promising.  It's the s2both function in the package uswsusp.  I've been running it a day and so far it works every time.  It takes 30 to 60 seconds to save the suspend image, depending on how many applications were open.  But, the resume takes less than 10 seconds.

regards,

---

