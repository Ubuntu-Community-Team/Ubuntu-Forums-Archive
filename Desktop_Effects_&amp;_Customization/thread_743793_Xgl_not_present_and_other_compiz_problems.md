---
title: "Xgl not present and other compiz problems"
date: 2008-04-03
forum: Desktop Effects &amp; Customization
---

### Post by yssida on 2008-04-03
Hi Everyone!

I have a Intel 965 chipset, and not heeding the advice of everybody I tried enabling compiz using the SKIP_CHECKS option in the terminal. This is what I got:

```

choking@Archangel:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: Window 0x3600049 (Mozilla Qu) sets an MWM hint indicating it isn't resizable, but sets min size 1 x 1 and max size 2147483647 x 2147483647; this doesn't make much sense.


```

What should I do? Should I also post a xorg.conf file? I don't quite know how to do that though...
Thanks.

---

### Post by yssida on 2008-04-03
bump...sorry...

---

### Post by yssida on 2008-04-04
help? ok, might as well make a longer and consolidated post...

---

### Post by andrewabc on 2008-04-07
Hello. I have same video card and was able to get 965 unblacklisted when I was using gutsy. I am not exactly sure on your problem or how to fix it.

Good news for you is that with Hardy that will be released in less than a month g965 chipset is no longer blacklisted and has some improvements for compiz.

So if you want you can get a beta of hardy live cd and see if stuff works for you without installing it. And wait until it is released April 24.

---

### Post by yssida on 2008-04-08
Yes, thank you. I actually received/downloaded Hardy Beta, before this and was quite confused. I thought that the earliest that 965 chipset be improved would be on Intrepid Ibex. So I was quite pleasantly surprised. Compiz still is very unstable on that build on my machine, so I disabled it and switched to Metacity.

---

