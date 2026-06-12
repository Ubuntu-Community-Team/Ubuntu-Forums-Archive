---
title: "Stellarium-0.8.0"
date: 2006-06-14
forum: Desktop Environments
---

### Post by snellgrove on 2006-06-14
Hi guys (& gals!)

I have a problem with Stellarium-0.8.0 if you hadn't guessed!

compiled and installed without a hitch, but running it as myself gives:
[img]http://static.flickr.com/64/167158488_92d9faa1e3_o.png[/img]

So, I go to try as root which gives me something worse!!
[img]http://static.flickr.com/75/167159704_b6ce9712f1_b.jpg[/img]

ctrl+c, ctrl+q, esc, alt+F4 etc nothing works, so its good ol' ctrl+alt+backspace which sorts it out again :(

Heres the config file (freshly made, by Stellarium-0.8.0) only things I have changed was max FPS from 10,000 down to a sensible 50, and turned off full-screen just in case that'd help but its the same with fullscreen as true as well.

```
[main]
version                        = 0.8.0

[video]
fullscreen                     = false
screen_w                       = 1024
screen_h                       = 768
bbp_mode                       = 32
horizontal_offset              = 0
vertical_offset                = 0
maximum_fps                    = 60
distorter                      = none

# when you use distorter = fisheye_to_spheric_mirror
# you must set [projection] type = fisheye

[projection]
type                           = stereographic
viewport                       = maximized
```

Now, OpenGL and all the other things are configured just fine as Stellarium-0.7.1 from the repositories works just fine, and I didn't see anything problematic thrown up by the ./configure, but I want the latest features :p

---

