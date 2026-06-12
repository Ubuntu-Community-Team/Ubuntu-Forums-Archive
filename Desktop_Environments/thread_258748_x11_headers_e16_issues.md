---
title: "x11 headers? e16 issues"
date: 2006-09-16
forum: Desktop Environments
---

### Post by doktorZee on 2006-09-16
I am trying to compile the latest release of Enlightenment 0.16.8 I believe.

It appears that some of the x11 headers are not present.
This also seemed to be an issue on Ubuntu HH
[http://ubuntuforums.org/showthread.php?t=92885](http://ubuntuforums.org/showthread.php?t=92885)

draw.c:620:36: error: X11/bitmaps/flipped_gray: No such file or directory
draw.c:621:28: error: X11/bitmaps/gray: No such file or directory
draw.c:622:29: error: X11/bitmaps/gray3: No such file or directory
draw.c: In function ‘DrawEwinShape’:
draw.c:651: error: ‘flipped_gray_bits’ undeclared (first use in this function)
draw.c:651: error: (Each undeclared identifier is reported only once
draw.c:651: error: for each function it appears in.)
draw.c:652: error: ‘flipped_gray_width’ undeclared (first use in this function)
draw.c:652: error: ‘flipped_gray_height’ undeclared (first use in this function)
draw.c:654: error: ‘gray_bits’ undeclared (first use in this function)
draw.c:654: error: ‘gray_width’ undeclared (first use in this function)
draw.c:655: error: ‘gray_height’ undeclared (first use in this function)
draw.c:657: error: ‘gray3_bits’ undeclared (first use in this function)
draw.c:657: error: ‘gray3_width’ undeclared (first use in this function)
draw.c:658: error: ‘gray3_height’ undeclared (first use in this function)
make[3]: *** [draw.o] Error 1

---

