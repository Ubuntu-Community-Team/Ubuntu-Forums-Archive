---
title: "Danger from the Deep error"
date: 2009-10-18
forum: Gaming &amp; Leisure
---

### Post by Tom_Keser on 2009-10-18
Hi all,

I am trying to run Danger from the Deep from Terminal.  I get this error message - 

"thomas@thomas-laptop:/usr/games$ dangerdeep
dangerdeep: error while loading shared libraries: libSDL_net-1.2.so.0: cannot open shared object file: No such file or directory"

- what is libSDL_net-1.2.so.0?

---

### Post by Perfect Storm on 2009-10-19
It's part of SDL net library.

```
sudo apt-get install libsdl-net1.2
```

---

### Post by Tom_Keser on 2009-10-20
> **Artificial Intelligence said:**
> It's part of SDL net library.

```
sudo apt-get install libsdl-net1.2
```

Thanks, I did that and now get this output in terminal:

Caught exception: invalid resolution requested!
Stack trace: (5 frames)
0x8070202 in dangerdeep at ??:0
0x806d431 in dangerdeep at ??:0
0x806d4f1 in dangerdeep at ??:0
0xb7b66775 in __libc_start_main at ??:0
0x804e6a1 in dangerdeep at ??:0

Any clues?

---

### Post by trytenn on 2009-10-30
I know it's a old thread but it came up for me when i searched the google. I had the same problem and maby someone else have it to. The default resolution was to big on my netbook (1024X700 something). So I changed the resolution-settings in the file 
~/.dangerdeep/config
I know 1024x600 and 800x600 will work. Try one of them and you can then change the resolution from the menu in the game. It looks lika a really intresting game so I'm gonna try it out now.

---

### Post by Tom_Keser on 2009-12-13
Thanks.  I am on a Dell mini so I set the screen resolution to 800 x 600 and the game fired right up and worked.  Excellent graphics.

---

