---
title: "Wrong resolution options after a monitor test.  I searched and tried other threads!"
date: 2009-12-30
forum: Desktop Environments
---

### Post by aj_the_first on 2009-12-30
I plugged a monitor into my Toshiba satellite A215 laptop, and the laptop now doesn't have the correct screen resolution for itself.  The icons are in the wrong areas, and the general desktop environment is not as I set it.
The main issue is screen resolution.  The option for my screen has disappeared from the options, (1280x800) and I have tried to add it as an option to the xorg.conf file, restarted numerous times, and still the problem has not changed.

I went through all the steps shown here:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
and all the steps mentioned in post #3 on this thread.
[http://ubuntuforums.org/showthread.php?t=1112186&highlight=size+1280x800+modes](http://ubuntuforums.org/showthread.php?t=1112186&highlight=size+1280x800+modes)

Neither works.  Terminal doesn't give any errors, accepts all my inputs, and it all seems like it should work, but nothing changes.  My xorg.conf file even shows that 1280x800 is the only option, but in the GUI, and using the xrandr command, it is not a settable option.

This is really confusing that it wouldn't revert to odd settings after the monitor was unplugged, and even worse, that it now can't re-recognize its own hardware on a restart, nor use the only settable option in the xorg.conf file.
How can I get my screen resolution back?

Thanks,
AJ

---

### Post by aj_the_first on 2009-12-30
I just tried this with a restart, and no change
[http://ubuntuforums.org/showthread.php?t=588005](http://ubuntuforums.org/showthread.php?t=588005)

---

### Post by aj_the_first on 2009-12-30
Okay, using some slightly modified data from ubuntu's wiki, I was able to properly add the correct 1280x800 resolution and add it to a custom xorg.conf file, and it is now available along with a 1280x7xx resolution, so it works, it is just odd that before I had a default xorg file, and now it has to be modified to work.

---

