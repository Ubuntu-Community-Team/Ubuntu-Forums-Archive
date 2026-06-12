---
title: "Evolution is hogging memory"
date: 2007-01-09
forum: Desktop Environments
---

### Post by bart34 on 2007-01-09
I have found memory in use by programs getting very high and am trying to find what is doing it.
Running nothing (on screen anyway)      - 15% prog   20% cache
Running only Evolution                           - 20%          20%
Getmail 3 more times (no message)       - 35%          20%
Getmail + 4 times                                  - 40%          20%
Getmail +1 time                                    - 45%           20%
Getmail +2 times                                  - 50%           20%
Later usage went right up to 95% prog and 5% cache! Somewhere about this point the disc started thrashing around. Swapping memory into disc space I suppose. 

What goes on? Is Evolution not releasing memory after each call for new mail? Is this normal or can you duplicate it? What can I do to keep my pc running like Linux and not bogging down like Windows? 

I'm running Ubuntu 6.10 & Evolution 2.8.1

---

### Post by Spin Doctor on 2007-01-09
Ok, I am by no means an expert in this field. But this is what I know about memory and Linux systems.

In a Linuxsystem, the internal memory is by design meant to be used. Because of this design, the Linux system creates buffers in the internal memory. So when you check how much memory you have left, you are shocked to see not much left. 

Instead of using ```
top
``` to find your free memory, use the command ```
free
```Look for the amount that is written at: buffers/cache under the free column.

---

### Post by bart34 on 2007-01-13
This is what I got after restarting Evolution and hitting getmail button several times. The image shows how memory "usage' went up every time I hit the button.
[IMG]http://members.shaw.ca/bart34b/sysmonitor-2.jpg[/IMG]

At the same time, I got this:
john@john:~$ free
             total       used       free     shared    buffers     cached
Mem:        743244     731576      11668          0       8776     138380
-/+ buffers/cache:     584420     158824
Swap:       979956     170388     809568
Thanks for your help. John

---

### Post by Spin Doctor on 2007-01-15
Are you experiencing the system slowing down because of the memory issue? 

I would not be surprised with a memory bug in Evolution. I have found many other bugs...but still use it every day.... Looking forward to next upgrade with Fiesty.

---

### Post by bart34 on 2007-01-16
Yes the system bogs right down until I close Evolution. It even makes it hard to shut the thing down sometimes! I have stopped calling for newmail every couple of minutes and now do it manually. This way the memory usage doesn't creep up when I'm not looking. I'll wait for a new version too I guess. Thanks.

---

