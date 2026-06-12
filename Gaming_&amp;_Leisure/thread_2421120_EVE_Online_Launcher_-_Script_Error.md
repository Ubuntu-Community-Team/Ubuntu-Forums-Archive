---
title: "EVE Online Launcher - Script Error"
date: 2019-06-16
forum: Gaming &amp; Leisure
---

### Post by gargarr on 2019-06-16
Hey everyone,

I was hoping to bring this to the community's attention and ask for some help in understand what this error is trying to tell me.

******@changed:~/Downloads/evelauncher$ ./evelauncher.sh 
QObject::startTimer: Timers can only be used with threads started with QThread
/home/******/Downloads/evelauncher/./evelauncher: symbol lookup error: /usr/lib/x86_64-linux-gnu/libGLX_mesa.so.0: undefined symbol: xcb_dri3_get_supported_modifiers

The most I have been able to find, thus far, is a GitHub post here:

[https://github.com/maxrd2/subtitlecomposer/issues/117](https://github.com/maxrd2/subtitlecomposer/issues/117)

I am pretty basic and new learner... :( Sorry if this question is super basic.

Thank you for your help! :)

---

### Post by mastablasta on 2019-06-18
look slike a driver error or something related to GPU.

ok it's actually a library. the library is either missing or should not be there.


[LIST]
[*]libxcb-dri3.so.0
[*]libxcb-dri2.so.0
[/LIST]

---

