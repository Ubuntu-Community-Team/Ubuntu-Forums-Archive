---
title: "Re-paint ghosting"
date: 2005-06-02
forum: Desktop Environments
---

### Post by veelivar on 2005-06-02
I'm noticing that when I drag windows around the desktop I'm getting alot of re-paint problems where teh window is not repainting fast enough.

Any one know how to fix this?

I do have my card (ATI 9800 pro) set up now, fglrxinfo reports right card.

Dan.

---

### Post by veelivar on 2005-06-03
Sorry I don't like bumping my own stuff but things seem to move so fast on these boards stuff can get missed.  Even I have a problem finding my own posts...

Anyway, does anyone have anyideas how to fix this?  Or have I put it in the wrong forum?

Cheers,
Dan.

---

### Post by shakin on 2005-06-03
I'm 90% sure your video driver is wrong. What's the driver name in xorg.conf? It should be 'fglrx', but you can also try 'ati' to see if that fixes the ghosting problem (though it will kill your 3d performance).

If you've got the fglrx driver installed and it looks correct in xorg.conf, I suggest backing up xorg.conf and running fglrxconfig to generate an XF86Config file, then renaming that file to xorg.conf.

---

### Post by veelivar on 2005-06-03
Thanks for the reply.

It is currently 'fglrx' in xconf (I know cos I had some fun and games setting it up earlier in the week).

[stupid question alert] what is the difference between XF86Config and xorg?

I'll try what you suggested when I get back to my box.  

Is it looking like I'm going to have a choice of either good 3d and bad 2d windows support or vice-versa?

Cheers,
Dan.

---

