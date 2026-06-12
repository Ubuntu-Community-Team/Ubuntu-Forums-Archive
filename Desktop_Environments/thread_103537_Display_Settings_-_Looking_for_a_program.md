---
title: "Display Settings - Looking for a program"
date: 2005-12-14
forum: Desktop Environments
---

### Post by Noelinho on 2005-12-14
I have quite an old monitor, which is quite dark. I'm am going to replace it - but not yet. In Windows, I use my NVidia graphics card settings to alter gamma etc... to alter the brightness of the screen.

What options are available to do this under Breezy?

---

### Post by Ampersand on 2005-12-14
You can use nvidia-settings to change brightness, otherwise you can use
```
xgamma -gamma n
```
Where n is a number (1 is default). I find about 1.4 or 1.5 works quite well.

---

### Post by Noelinho on 2005-12-14
Thanks, works a treat :)

---

### Post by Noelinho on 2005-12-14
The only other thing I'd like to ask on this matter - how would I save this change, so that it invokes it on startup?

---

### Post by Noelinho on 2005-12-15
Anyone?

---

### Post by Cordate on 2005-12-28
You could make a script that would run the command, and have the script run each time at boot. [This thread]('http://ubuntuforums.org/showthread.php?t=108909') has info on how to do that. And if you need it, LinuxCommand.org has a nice tutorial on writing shell scripts. :)

---

