---
title: "calibrate nunchuck?"
date: 2009-10-11
forum: Gaming &amp; Leisure
---

### Post by dakilla on 2009-10-11
My nunchucks needs to be calibrated, any one knows where i can do this?
they think its "left" when joystick is in "center".
happens on booth my wiimotes/nunchucks. using Xwii 2.8.

they does not work with wmgui or wminput, i had to change the exp-id code in wiiuse_internal.h for my nunchucks in Xwii because they got another ID :S
changed to:
#define EXP_ID_CODE_NUNCHUK	0xa4200000

and now they works fine, but as i said earlier, they need to be calibrated.

---

