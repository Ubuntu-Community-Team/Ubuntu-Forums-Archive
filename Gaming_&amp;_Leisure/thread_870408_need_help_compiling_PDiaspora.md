---
title: "need help compiling PDiaspora"
date: 2008-07-25
forum: Gaming &amp; Leisure
---

### Post by 900donuts on 2008-07-25
I saw the game PDiaspora on the UGA and decided to give it a shot.

I followed the very small README file and this is what I got.

```
 memory.c:146: warning: deprecated conversion from string constant to &#8216;char*&#8217;
memory.c:147: warning: deprecated conversion from string constant to &#8216;char*&#8217;
/usr/bin/ld: cannot find -lXinerama
collect2: ld returned 1 exit status
make: *** [client] Error 1

```

this is only the last 5 lines there is a lot more.

So how do i fix this?

thanks in advance:)

---

### Post by Radioactiveroach on 2009-10-10
I actually just typed in xinerama in synaptics and installed the dev version of xinerama then it compiled with quite an array of warnings most of them saying "warning: deprecated conversion from string constant to ‘char*’". When I tried to run it it gave me an error saying it could not find font/arial.ttf so I made a symbolic link to /usr/share/fonts/truetype/msttcorefonts of course none of this matters cuz the array of warnings came back to haunt me when the program killed itself with a segmentation fault.

---

