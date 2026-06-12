---
title: "Solitaire Crashing System"
date: 2009-01-25
forum: General Help
---

### Post by klausner on 2009-01-25
Problem with /usr/games/sol randomly crashing 8.10 Intrepid. It does this in both Klondike and Freecell modes. Happens only occasionally, but when it does, always while dragging a card.

Seems to crash the X server, as the screen goes to garbage, then blank, then garbage. Seems to be trying to correct itself, but doesn't. Ctl-Alt-Backspace doesn't help.

Tried downloading newer Intel driver, but made no difference.

---

### Post by Crafty Kisses on 2009-01-25
Can you post your X logs?
```
/var/log/Xorg.0.log
```

---

### Post by klausner on 2009-01-25
Here it is. Had to zip it up for the forum to accept it.

---

### Post by klausner on 2009-02-02
Bump. New X log attached.

---

### Post by klausner on 2009-02-19
Bump. Still hoping for an answer.
](*,)

---

### Post by klausner on 2009-05-14
***Still*** hoping for an answer ](*,)

---

### Post by dcottingham on 2009-05-14
A bit of googling turned up a bug report on launchpad that seems to resemble your problem:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/292761](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/292761)
If you page on down to comment 22, by Cosmin Roman, he presents a workaround that he says fixed it for him.  Also, comment 26 by Karel Kolman gives a link to a patch that he says fixed it for him.

---

### Post by klausner on 2009-05-14
> **dcottingham said:**
> A bit of googling turned up a bug report on launchpad that seems to resemble your problem:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/292761](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/292761)
If you page on down to comment 22, by Cosmin Roman, he presents a workaround that he says fixed it for him.  Also, comment 26 by Karel Kolman gives a link to a patch that he says fixed it for him.

Thank you for the response. I looked at the workaround, but I only have one device defined, so that doesn't seem to be an option. As for the patch, I'm a bit reluctant to undertake rebuilding xorg. Since this bug was closed in 7.4, does that mean that it is fixed in 7.5, and that installing 7.5 would fix the problem?

---

### Post by dcottingham on 2009-05-15
Far as I can tell, there is no 7.5 yet.  It might mean that an updated 7.4 would work. But I think 8.10 came with xorg 7.4, so it seems like you should have the latest official patches already. I suppose you might try the 9.04 live cd and see if it shows the same bad behavior.

If you google around a little you can find tutorials on patching the kernel. It's more tedious than difficult.

BTW, is this a laptop?

---

### Post by klausner on 2009-05-15
> **dcottingham said:**
> Far as I can tell, there is no 7.5 yet.  It might mean that an updated 7.4 would work. But I think 8.10 came with xorg 7.4, so it seems like you should have the latest official patches already. I suppose you might try the 9.04 live cd and see if it shows the same bad behavior.

If you google around a little you can find tutorials on patching the kernel. It's more tedious than difficult.

BTW, is this a laptop?

Yes, this is a laptop. I have eschewed 9.04 because of all the negative reports about how poorly it works with Intel graphics.

Thanks again.

---

### Post by dcottingham on 2009-05-15
Maybe you should revisit your conclusion that the first workaround (using xrandr) is not applicable to you. I took another look in your log file, and it seems to say you have outputs VGA, LVDS, and TMDS, just like the example in the workaround. It might be worth running xrandr and seeing if it agrees with this list, and if so trying the xorg.conf in the workaround.

---

### Post by klausner on 2009-05-15
> **dcottingham said:**
> Maybe you should revisit your conclusion that the first workaround (using xrandr) is not applicable to you. I took another look in your log file, and it seems to say you have outputs VGA, LVDS, and TMDS, just like the example in the workaround. It might be worth running xrandr and seeing if it agrees with this list, and if so trying the xorg.conf in the workaround.

xrandr does show all three. but xorg.conf only has one device. Minus the comments, this is my xorg.conf file:
```
Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

---

### Post by dcottingham on 2009-05-15
It appears magic is in using the xorg.conf to apply the phrase

Option "Ignore" "true"

to the outputs you're not using. I believe it would be worth just replacing your xorg.conf with the one from  the workaround. (Save a copy of yours first.)  Just to see what happens.

---

### Post by klausner on 2009-05-15
> **dcottingham said:**
> I believe it would be worth just replacing your xorg.conf with the one from  the workaround. (Save a copy of yours first.)  Just to see what happens.

If I read the post right, the file he show is his *before* file. How would arbitrarily removing one of the lines make a difference? Also, his BUSID probably isn't correct for my system.

---

### Post by klausner on 2009-05-16
I took a chance, and installed xorg version 1.7.4-5ubuntu18 from the Jaunty repository, in the expectation that it would have the bug fix. Today I found that it didn't solve my problem. Either the new version doesn't have the bug fix, or the fix doesn't solve this.
:(

---

