---
title: "Problem starting xgl"
date: 2006-10-11
forum: Desktop Environments
---

### Post by Saubazi on 2006-10-11
I have 64 bit Dapper and now I have been trying to concentrate on getting xgl to run. I am not able to get the session to start it comes always back to login prompt.

I also tried /etc/init.d/gdm stop and then 
 Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer && DISPLAY=:1
but with no luck among the otherthings it said that fullscreen option does not exist or something so I suspect that the command is fundamentally wrong.

As a further point apt-get install beryl-core gives me:
$ sudo apt-get install beryl-core
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package beryl-core

Is this 64bit thing? Can I use compiz instead?

I have ati card:

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.5814 (8.25.18)

render should be o.k but otherwise I am lost...

---

### Post by Saubazi on 2006-10-11
Correction first hurdle is past. I tried once more stopping gdm and trying Xgl commands - I noticed an error about missing libglitz-glx.so.1 library which I believe has something to do with 64bit (hasty google search revealed). 
I installed sudo apt-get install libglitz-glx1
 and now I seem to be running xgl session.

Where do I go from here with that beryl problem, though?

---

