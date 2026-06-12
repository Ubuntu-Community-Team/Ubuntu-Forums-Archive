---
title: "1525n touchpad not working in 8.04"
date: 2008-05-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tylersontag on 2008-05-02
A week ago i upgraded to 8.04 on my Dell Inspirion 1525.  I was quite pleased initially, alot of the video problems stemming from the embedded video card were fixed.  Videos played, my screensavers worked correctly.  As i said, i was happy i could enjoy some of the prettier screensavers.

I was watching TV and hadn't used the top in a while, i look over and flocks is running, i stared for a moments, its quite mezmerizing.  THhen my screen froze, black with a multi-colored static.  When i rebooted my touchpad wasn't working.  i looked for some info but found nothing.  i went out that night, when i got back it was working again.  Alas the next morning it wasn't working and ive been on a USB mouse ever since.

I talked with dell, ran some diagnostics and determined its not hardware related.  He had me try to rebuild my xorg with "sudo dpkg-reconfigure xserver-xorg" but it didn't help, and whats more, apparently it doesn't function the same as the previous build, or at least not on mine.

I was alerted to a similar but with 8.04 regarding the touchpad, [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/173411](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/173411) but thats only regard to the side scroll bar not working.  i've found this: [https://answers.launchpad.net/ubuntu/+question/31505](https://answers.launchpad.net/ubuntu/+question/31505) which seems to be the same problem.   Any ideas?

---

