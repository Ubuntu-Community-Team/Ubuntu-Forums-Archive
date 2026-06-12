---
title: "No Sound"
date: 2005-10-14
forum: Desktop Environments
---

### Post by greengrass on 2005-10-14
I have a 133ghz pentium with stardard ubuntu install    10G harddrive  64M RAM   I cant hear any sounds.   How do you configure it?

---

### Post by xingmu on 2005-10-14
So is the problem something like: You play a sound file with no errors or other problems, but you just don't hear any sound?

Try opening a terminal and type:```
alsamixer
```  This will displays the volume levels for various in/output devices.  Check that the Master is *not* turned OFF.  If it is, you can toggle it by pressing the key 'm'.

ALTERNATIVE METHOD: The above solution should be exactly the same as opening Applications > Sound & Video > Volume control.  Go to File > Change Device and select ... (AlsaMixer).  Check that the little speaker icon below the Master volume control does not have a red 'X' over it.  You can click it with your mouse to toggle it.

I am assuming:

1. Your speakers/headphones are plugged in and working
2. Your external volume control is not turned all the way down.
3. Your sound card is installed and working

---

### Post by az on 2005-10-15
You probably have old hardware that cannot be probed.  This should help:

[https://wiki.ubuntu.com/forum/hardware/OldSoundCard](https://wiki.ubuntu.com/forum/hardware/OldSoundCard)

---

