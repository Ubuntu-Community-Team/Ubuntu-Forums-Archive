---
title: "General freeze in lubuntu"
date: 2011-06-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by spoketire on 2011-06-09
I have been running regular ubuntu for a while on a dell dimension 4600, and decided to try lubuntu. Ubuntu worked very well with virtually no problems. In lubuntu I am experiencing some general graphics issues where squares of junk will appear on certain gui elements, but more importantly, if I try to do too much, everything will lock up except the mouse. I think this might be an X crash, but I'm not sure. I cannot switch to another virtual terminal with Ctrl+Alt+F#.

I'm not sure where to start in troubleshooting this. I am willing to post config files if requested. Any help is appreciated.

---

### Post by kirkous on 2011-06-10
iam experiencing the same problem on my old Siemens Amilo pro 2030. I upgraded to lubuntu 11.04 yesterday from ubuntu 10.10. Guess ill downgrade :(

---

### Post by spoketire on 2011-06-10
I wouldn't give up that fast.

Since I originally posted, I ran the first upgrade, and that got rid of the garbled graphics, but not the freezes. I had one freeze (which seemed to be a result of doing too much at once) from which I was able to recover by switching to another tty and running "pkill X".

By the way, my graphics controller is intel 82865G integrated, so it's probably using the open source i915 driver (not sure how to check). Additional Drivers doesn't show anything.

---

### Post by spoketire on 2011-06-10
> **kirkous said:**
> iam experiencing the same problem on my old Siemens Amilo pro 2030. I upgraded to lubuntu 11.04 yesterday from ubuntu 10.10. Guess ill downgrade :(

If you end up going back to ubuntu, you could try installing lxde onto it. That might work.

---

