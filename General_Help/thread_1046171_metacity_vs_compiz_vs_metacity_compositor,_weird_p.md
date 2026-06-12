---
title: "metacity vs compiz vs metacity compositor, weird performance"
date: 2009-01-21
forum: General Help
---

### Post by oedipuss on 2009-01-21
I'm getting some weird results from running glxgears with compiz & metacity.


Does this seem right?
**Compiz**
```
26916 frames in 5.0 seconds = 5383.068 FPS
27144 frames in 5.0 seconds = 5428.637 FPS
27156 frames in 5.0 seconds = 5431.023 FPS
```

**Metacity**
```
51527 frames in 5.0 seconds = 10305.252 FPS
50001 frames in 5.0 seconds = 10000.022 FPS
51890 frames in 5.0 seconds = 10377.996 FPS

```
Dramatic increase, nothing strange here though. 

BUT
**Metacity with compositing**
```
4062 frames in 5.0 seconds = 812.263 FPS
4088 frames in 5.0 seconds = 817.449 FPS
4091 frames in 5.0 seconds = 818.032 FPS
```
HUH?? This can't be right, why is it so much slower? Is there something else going on, or just glxgears reporting wrong fps somehow? 
Were it stuck at 60fps I'd guess it was vsync related, but it's not even constant.

I'm using an nvidia 7600 , drivers v. 180.11

---

