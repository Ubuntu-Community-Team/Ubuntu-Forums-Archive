---
title: "after upgrade to 23.10 the suspend not working"
date: 2023-11-14
forum: Desktop Environments
---

### Post by bodnarlajoska on 2023-11-14
Hi,
There was no any issue with my system and I upgraded to 23.10.
After the upgrade the suspend don't working well.
It is not waking up!
I can say every 2 or 3 times when I close the lid and the computer is going to suspend state it will stay in suspend state.
With the long push on the power button I can power-off my computer and I lose every ongoing work.

I tried: echo mem | sudo tee /sys/power/state
it is working and in this case every time my computer is come back from suspend state as expected.

do you know what is the problem ?
Do you know what program / systemd is running when I close the lid ?

thanks is advance!

---

