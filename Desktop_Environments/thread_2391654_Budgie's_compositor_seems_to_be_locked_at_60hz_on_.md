---
title: "Budgie's compositor seems to be locked at 60hz on a 144 hz monitor"
date: 2018-05-11
forum: Desktop Environments
---

### Post by daaaniii on 2018-05-11
Hello folks,
after distro-hopping I finally tried out ubuntu 18.04 Budgie - everything works out of the box but one thing is driving me sort of crazy.
First, I have a xeon cpu and a nvidia gtx 770, so theres' only one graphics card inside my pc. So I tried both, nouveau drivers (open-source) and the nvidia proprietary closed source drivers. Both work actually, but usually I'm sticking to the prop drivers because of the performance difference.
So when I set the display refresh rate to 144hz, it seems to work well because the mouse feels faster / more responsive compared to 60hz. But when I drag windows around or scroll in any application which has smooth-scrolling enabled (ex. in firefox) - you can tell it's 60hz because theres no difference like when I set the refresh rate to 60hz. So I guess it's the compositor inside of budgie-wm, seems still to be based on libmutter - I have no idea if it's a bug or not, but it's the only thing holding me back from ubuntu budgie (and budgie is more me the best DE).

PS: I also installed i3 on ubuntu budgie. Since theres no internal compositor everything on 144hz was smooth as butter, so I bet it's definitely the compositor of budgie.

So, is there an actual fix or is this a known "bug"?

regards

---

### Post by dino99 on 2018-05-12
i feel you might have a few 'not ready' hardware/software to support 144 hz yet: DE, kernel, cpu/gpu, ram, screen port used/cord . If only one of these elements is not able to support 144 hz, then you only get the default 60 hz.
[https://www.reddit.com/r/linux_gaming/comments/4qzd52/144hz_on_linux/](https://www.reddit.com/r/linux_gaming/comments/4qzd52/144hz_on_linux/)
[https://wyldeplayground.net/144hz-refresh-rate-ubuntu-18-04-with-nvidia/](https://wyldeplayground.net/144hz-refresh-rate-ubuntu-18-04-with-nvidia/)

---

