---
title: "Access limited to first 64K of framebuffer"
date: 2006-06-13
forum: Desktop Environments
---

### Post by JR Canada on 2006-06-13
I cannot access more than the first 64K of a display framebuffer, but don't know what I am doing wrong.

It should be possible to access the display framebuffer through /dev/fb0 using any one of several techniques (opening a file, mapping the memory with mmap, or just cp from the command line to capture the screen to a file).

When I use the command "cp /dev/fb0 file.raw", I get a file of only 64K bytes.  I have tried this on two different computers with different display drivers and resolutions (1280x1024, and 640x480), both using Ubuntu 6.06, and on one other computer using Ubuntu 5.10 at 1024x768.  All do exactly the same thing, producing only a 64K byte output file.  

The same thing happens when I try to read from the framebuffer using C, either opening the display as file or by mapping the memory: Only the first 64K is available (any attempt to map more is shown as invalid).  When mapping the memory to write to the screen, I can see the pixels change starting at the upper left, but again I can access only the first 64K.

Using the 'Take Snapshot' command from the menu appears to capture the whole screen on all three systems with no problem.  Can anyone please tell me what I am doing wrong?  Thank you!

---

