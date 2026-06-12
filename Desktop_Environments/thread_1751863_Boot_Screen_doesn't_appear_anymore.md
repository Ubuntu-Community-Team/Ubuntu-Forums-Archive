---
title: "Boot Screen doesn't appear anymore"
date: 2011-05-07
forum: Desktop Environments
---

### Post by Elite6809 on 2011-05-07
Hello everyone. I'm fairly new to Ubuntu and I like it a lot. However, there's a graphical error which started to happen after the very first bootup. The startup screen (the purple one with the 5 dots that appear) isn't showing anymore. It is replaced by some console technical guff scrolling down my screen (which isn't a problem, because Ubuntu itself works fine, but it just looks a bit rough). Again, on shutdown, it displays some amalgamated mix of more technical jargon, and a terribly lo-res version of the shutdown screen.
Is there any way I can fix this?
Thanks for replying.

---

### Post by Vuk Serbia on 2011-05-07
While I was using Ubuntu 10.10 this happened to me after I installed ATI drivers.
I don't have this problem with 11.4. 
Which release are you using?

---

### Post by Elite6809 on 2011-07-08
Sorry for the bump - it's been a while now and I know a hell of a lot more about Ubuntu. I'm on Natty and I reckon it's a problem with Plymouth and nVidia proprietary drivers.

---

### Post by Blasphemist on 2011-07-08
You'll need to do some grub edits as natty changed the handoff of video modes between bios, grub, the kernel and X. Please see this thread, mainly the first 3 posts for troubleshooting your issue and making the changes. You'll be able to try things with temporary edits and when you find the right thing, you can make them permanent.
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by Elite6809 on 2011-07-09
> **Blasphemist said:**
> You'll need to do some grub edits as natty changed the handoff of video modes between bios, grub, the kernel and X. Please see this thread, mainly the first 3 posts for troubleshooting your issue and making the changes. You'll be able to try things with temporary edits and when you find the right thing, you can make them permanent.
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Thanks! I installed startupmanager and it fixed my problems. Thanks to you!

---

