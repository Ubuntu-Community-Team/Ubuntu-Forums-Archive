---
title: "Compiz volume overlay icon has changed to low res image"
date: 2010-12-03
forum: Desktop Environments
---

### Post by gabe_rosser on 2010-12-03
Hi all,

I upgraded to 10.10 recently and my Compiz volume icon has changed.  I'm talking about the overlay icon that pops up when I use keyboard shortcuts to change the volume.  It is still a speaker icon in a grey box, but the icon used to be the right resolution and now it is an ugly low resolution image, which has been interpolated to a larger size.

See the atttached screenshot - the box actually appears in the centre of the screen but I cut the picture down.

Any ideas how to fix it?

Thanks,

G

---

### Post by stallmer on 2011-09-22
This is an old post, but I'm replying because it is the first result on Google, and none of the Google hits had an answer.

I had the same problem, but I found out that the reason was that I had uninstalled the package "[FONT="Courier New"]notify-osd[/FONT]" when fooling around with other desktop environments.

To fix:
```
sudo apt-get install notify-osd
```

---

